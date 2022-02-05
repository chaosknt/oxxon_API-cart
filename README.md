# Oxxon Comercialización & Distribución


# Introduction

This document contais all necessary data to integrate  `Oxxon Comerializacion & Distrubición` with external providers.


# API Documentation

Base URL: `http://tienda.oxxon-cd.com/api`

## Add new Customer

### Description

Use to add new customer. This process is asynchronous. The new customer will be approved by a agent of `Oxxon Comerializacion & Distrubición` and it could take beetwen 1 hour to 5 to get the response. The new customer Confirmation will send by email.

> Warning: This method require basic auth through header. You have to contact with the tecnical area to gets your auth credentials.

## Request Format

<ul>
  <li>Path: <b>/cart/</b></li>
  <li>Method: <b>HttpPost</b></li>
 </ul>

## Headers 
<ul>
  <li>Content-Type: <b>multipart/form-data</b></li>
  <li>Accept-Encoding: <b>gzip, deflate, br</b></li>
  <li>Authentication: <b>basic user:pass</b> </li>
</ul>


## Form-Data

```
{
  METHOD: always be "CreateNewCustomer",
  newCustomer: {"string","string"}
}

```
### newCustomer keys description:

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Name
			</th>
			<th rowspan="8" align="left">
				Description
			</th>
      <th rowspan="8" align="left">
				Required
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">razonsocial</p>
			</td>
			<td>
				<p>Name with which an entity or commercial company is legally registered.</p>
			</td>
      <td>
				<p>true</p>
			</td>
		 </tr>		
    <tr valign="top">
			<td>
				<p align="left">dni</p>
			</td>
			<td>
				<p>Clave Única de Identificación Tributaria (cuit) or Documento Nacional de identidad (DNI)</p>
			</td>
      <td>
				<p>true</p>
			</td>
    </tr>
      <tr valign="top">
      <td>
				<p align="left">localidad</p>
			</td>
			<td>
				<p>The customer town.</p>
			</td>
      <td>
				<p>true</p>
			</td>
    </tr>
      <tr valign="top">
      <td>
				<p align="left">calle</p>
			</td>
			<td>
				<p>The customer street.</p>
			</td>
      <td>
				<p>true</p>
			</td>
      </tr>	  
       <tr valign="top">
       <td>
				<p align="left">altura</p>
			</td>
			<td>
				<p>The customer's house number.</p>
			</td>
      <td>
				<p>true</p>
			</td>
   </tr>	
   <tr valign="top">
      <td>
				<p align="left">entrecalles</p>
			</td>
			<td>
				<p>Streets between the custome'r house or some reference</p>
			</td>
      <td>
				<p>true</p>
			</td>
     </tr>	
       <tr valign="top">
      <td>
				<p align="left">telefono</p>
			</td>
			<td>
				<p>The customer phone number</p>
			</td>
      <td>
				<p>true</p>
			</td>
    </tr>	
   <tr valign="top">
      <td>
				<p align="left">rubro</p>
			</td>
			<td>
				<p>The customer bussiness type</p>
			</td>
      <td>
				<p>true</p>
			</td>
   </tr>	
    <tr valign="top">
        <td>
				<p align="left">condventa</p>
			</td>
			<td>
				<p>The customer invoce type, for example monotributista </p>
			</td>
      <td>
				<p>true</p>
			</td>
		 </tr>	
     <tr valign="top">
        <td>
				<p align="left">email</p>
			</td>
			<td>
				<p>The customer email.  </p>
			</td>
      <td>
				<p>true</p>
			</td>
		 </tr>		
     <tr valign="top">
        <td>
				<p align="left">horario</p>
			</td>
			<td>
				<p>The customer time to receive the shipping.</p>
			</td>
      <td>
				<p>true</p>
			</td>
		 </tr>		
		</tbody>
</table>

## Special considerations

### DNI

Must be unique. min length is 6. If Cuit is send, the min lenght is 10. `Do NOT include less sign (-) if you send CUIT`.

### HORARIO

The shipping time that we do is since 8 am to 15 pm.*

###  CONDVENTA

If the customer is not `consumidor final`, only must send the CUIT number when you send the DNI field.


## Response handling

Success/failure exits on the Interface API will be handled via HTTP status codes.

Successful request will get a HTTP 200.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseMessage” field.


## Sample Messages

### Create new Customer

Request:

url: ` http://tienda.oxxon-cd.com/api/cart/ `

```
{
  METHOD: "CreateNewCustomer",
  newCustomer: {
                "razonsocial":"gardelito SA",
                "dni":"30648839088",
                "localidad":"Burzaco",
                "calle":"Chacabuco",
                "altura":"1976",
                "entrecalles":"Esquina libertad",
                "telefono":"1535889858",
                "rubro":"kiosko",
                "condventa":"consumidor final",
                "email":"gardelito@gmail.com",
                "horario":"9 a 18"
              }
}
```


