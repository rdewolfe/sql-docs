---
title: "Generate an Inline XDR Schema | Microsoft Docs"
description: View information about generating an inline XDR schema and about the deprecation of the XMLDATA directive in the FOR XML clause.
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: sql
ms.prod_service: "database-engine"
ms.reviewer: ""
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords: 
  - "XDR schemas [SQL Server]"
  - "inline XDR schema generation [SQL Server]"
  - "XMLDATA option"
  - "FOR XML clause, inline XDR schema generation"
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
author: MikeRayMSFT
ms.author: mikeray
---
# Generate an Inline XDR Schema
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  The **XMLDATA** directive in FOR XML returns an inline XDR schema together with the query result. However, the XDR schema does not support all the new data types and other enhancements introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions. Instead, you can request an inline XSD schema by using [the XMLSCHEMA directive](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
> [!IMPORTANT]  
>  The XMLDATA directive to the FOR XML option is deprecated. Use XSD generation in the case of RAW and AUTO modes. There is no replacement for the XMLDATA directive in EXPLICIT mode. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Also note the following about the inline XDR schema support:  
  
-   If the FOR XML query result includes columns of **xml** type and you request an inline XDR schema, an error is returned. Inline XDR does not support these types.  
  
-   The **(n)varchar(max)** and **(n)varbinary(max)** types will be mapped to **(n)varchar(n)** and **varbinary(n)**, respectively.  
  
-   When compatibility mode is set to 90 or higher, **timestamp** values are considered as **varbinary(8)** data, are treated like binary data, and are returned in the result as follows:  
  
    -   Base 64 encoding is used when **binary base64** is specified.  
  
    -   URL encoding is used in AUTO mode when **binary base64** is not specified.  
  
  
