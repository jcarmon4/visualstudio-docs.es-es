---
title: 'Archivo XSD de muestra: Esquema de pedido de compra | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3a699ed1eecfbd41e40a84d185e4d1d7d45fa59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145185"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>Archivo XSD de muestra: Esquema de pedido de compra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El archivo XSD siguiente se usa en numerosos ejemplos de la documentación del Diseñador de esquemas XSD. Este archivo es un esquema de pedido de compra.  
  
```xml  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"   
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"   
          elementFormDefault="qualified">  
  <xsd:element name='comment' type='xsd:string'/>  
  
  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>  
  
  <xsd:complexType name='USAddress'>  
    <xsd:annotation>  
      <xsd:documentation>  
        Purchase order schema for Example.Microsoft.com.  
      </xsd:documentation>  
    </xsd:annotation>  
    <xsd:sequence>  
      <xsd:element name='name'   type='xsd:string'/>  
      <xsd:element name='street' type='xsd:string'/>  
      <xsd:element name='city'   type='xsd:string'/>  
      <xsd:element name='state'  type='xsd:string'/>  
      <xsd:element name='zip'    type='xsd:decimal'/>  
    </xsd:sequence>  
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>  
  </xsd:complexType>  
  
  <xsd:simpleType name='SKU'>  
    <xsd:restriction base='xsd:string'>  
      <xsd:pattern value='\d{3}\w{3}'/>  
    </xsd:restriction>  
  </xsd:simpleType>  
  
  <xsd:complexType name='Items'>  
    <xsd:sequence>  
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name='productName' type='xsd:string'/>  
            <xsd:element name='quantity'>  
              <xsd:simpleType>  
                <xsd:restriction base='xsd:positiveInteger'>  
                  <xsd:minInclusive value='1'/>  
                  <xsd:maxExclusive value='100'/>  
                </xsd:restriction>  
              </xsd:simpleType>  
            </xsd:element>  
            <xsd:element name='USPrice'  type='xsd:decimal'/>  
            <xsd:element ref='tns:comment'/>  
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>  
          </xsd:sequence>  
          <xsd:attribute name='partNum' type='tns:SKU'/>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  
  <xsd:complexType name='PurchaseOrderType'>  
    <xsd:sequence>  
      <xsd:element name='shipTo' type='tns:USAddress'/>  
      <xsd:element name='billTo' type='tns:USAddress'/>  
      <xsd:element ref='tns:comment' minOccurs='0'/>  
      <xsd:element name='items'  type='tns:Items'/>  
    </xsd:sequence>  
    <xsd:attribute name='orderDate' type='xsd:date'/>  
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>  
  </xsd:complexType>  
</xsd:schema>  
```
