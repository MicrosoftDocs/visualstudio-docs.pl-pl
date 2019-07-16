---
title: '&lt;fileassociation —&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b31ac34627b244cb61b6fdb5c6ca214675ec045
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150841"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileassociation —&gt; — Element (aplikacja ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa rozszerzenie pliku do skojarzenia z aplikacją.  
  
## <a name="syntax"></a>Składnia  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `fileAssociation` Element jest opcjonalne. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`extension`|Wymagane. Rozszerzenie pliku, który ma zostać skojarzony z aplikacją.|  
|`description`|Wymagany. Opis typu plików do użytku przez powłokę.|  
|`progid`|Wymagane. Nazwa, który unikatowo identyfikuje typ pliku.|  
|`defaultIcon`|Wymagane. Określa ikonę do używania z plików z tego rozszerzenia. Plik ikony musi być określona za pomocą [ \<Plik > Element](../deployment/file-element-clickonce-application.md) w ramach [ \<zestawu > Element](../deployment/assembly-element-clickonce-application.md) zawierający ten element.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element musi zawierać odwołanie do przestrzeni nazw XML "urn: schemas-microsoft-com:clickonce.v1". Jeśli `<fileAssociation>` element jest używany, musi być późniejsza `<application>` elementu w jego element nadrzędny [ \<zestawu > Element](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nie spowoduje zastąpienie istniejących skojarzeń plików. Aplikacja ClickOnce może jednak zmienić rozszerzenie pliku dla bieżącego użytkownika. Po odinstalowaniu tej aplikacji ClickOnce ClickOnce spowoduje usunięcie skojarzenia pliku dla użytkownika, a następnie ponownie skojarzenia komputera jest aktywny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `fileAssociation` elementów w aplikacji manifestu dla aplikacji edytora tekstu, wdrożone za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Ten przykładowy kod zawiera również [ \<Plik > Element](../deployment/file-element-clickonce-application.md) wymagane przez `defaultIcon` atrybutu.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
