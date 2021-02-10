---
title: '&lt;RelatedProducts — &gt; element (program inicjujący) | Microsoft Docs'
description: Element RelatedProducts definiuje inne produkty, które są zależne od lub są zawarte w bieżącym produkcie.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7987306d9f7fc25f9f9b783d5b0966ac5015ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949691"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts — &gt; element (program inicjujący)
`RelatedProducts`Element definiuje inne produkty, które są zależne od lub są zawarte w bieżącym produkcie.

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

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `RelatedProducts`Element jest elementem podrzędnym `Product` elementu. Nie ma atrybutów.

## <a name="dependsonproduct"></a>DependsOnProduct
 `DependsOnProduct`Element oznacza, że bieżący produkt zależy od określonego produktu i że nazwany produkt należy zainstalować przed bieżącym. Jest elementem podrzędnym `RelatedProducts` elementu. `RelatedProducts`Element może mieć jeden lub więcej `DependsOnProduct` elementów.

 `DependsOnProduct` ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`Code`|Nazwa kodu dołączonego produktu określona przez `ProductCode` atrybut `Product` elementu. Aby uzyskać więcej informacji, zobacz [ \<Product> element](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts`Element definiuje zero lub więcej `DependsOnProduct` elementów i nie ma żadnych atrybutów. `DependsOnProduct`Przed bieżącym produktem należy zainstalować co najmniej jeden z tych zestawów. `RelatedProducts`Element może mieć zero lub więcej `EitherProducts` elementów.

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct`Element oznacza, że produkt jest dołączony do bieżącej instalacji i nie wymaga osobnej instalacji. Jest elementem podrzędnym `RelatedProducts` elementu. `RelatedProducts`Element może mieć jeden lub więcej `IncludesProduct` elementów.

 `IncludesProduct` ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`Code`|Nazwa kodu dołączonego produktu określona przez `ProductCode` atrybut `Product` elementu. Aby uzyskać więcej informacji, zobacz [ \<Product> element](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Przykład
 Poniższy przykład kodu określa, że Instalator firmy Microsoft jest instalowany z .NET Framework i w związku z tym nie wymaga osobnej instalacji.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Zobacz też
- [\<Product> postaci](../deployment/product-element-bootstrapper.md)