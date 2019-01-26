---
title: '&lt;RelatedProducts&gt; — Element (program inicjujący) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e04cc8a351ed99ec0b477b2db5052ac94b56054
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036137"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; — element (program inicjujący)
`RelatedProducts` Element definiuje innych produktów, które zależą od lub znajdują się w bieżącym produkcie.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `RelatedProducts` Element jest elementem podrzędnym `Product` elementu. Go nie ma żadnych atrybutów.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct` Element oznacza, że bieżącego produktu zależy od wskazanego produktu i że wskazanego produktu powinien zostać zainstalowany przed bieżącym. Jest elementem podrzędnym `RelatedProducts` elementu. A `RelatedProducts` element może mieć co najmniej jeden `DependsOnProduct` elementów.  
  
 `DependsOnProduct` ma następujący atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Code`|Nazwa kodu produktu uwzględniona, określony przez `ProductCode` atrybutu `Product` elementu. Aby uzyskać więcej informacji, zobacz [ \<produktu > Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts` Element definiuje zero lub więcej `DependsOnProduct` elementów, a nie ma żadnych atrybutów. Co najmniej jeden `DependsOnProduct` w tym zestawie musi zostać zainstalowany przed bieżącego produktu. A `RelatedProducts` element może mieć zero lub więcej `EitherProducts` elementów.  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct` Element oznacza znajduje się w bieżącej instalacji produktu i nie wymagają oddzielnej instalacji. Jest elementem podrzędnym `RelatedProducts` elementu. A `RelatedProducts` element może mieć co najmniej jeden `IncludesProduct` elementów.  
  
 `IncludesProduct` ma następujący atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Code`|Nazwa kodu produktu uwzględniona, określony przez `ProductCode` atrybutu `Product` elementu. Aby uzyskać więcej informacji, zobacz [ \<produktu > Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu Określa, że Microsoft Installer został zainstalowany z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]i w związku z tym nie wymagają oddzielnej instalacji.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [\<Produktu > element](../deployment/product-element-bootstrapper.md)