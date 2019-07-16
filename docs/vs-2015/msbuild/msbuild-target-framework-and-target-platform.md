---
title: Platforma docelowa programu MSBuild i platformy docelowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a550b4a6634604594da0893e3f420fd9c38ca3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181019"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Platforma docelowa programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skompilować projekt, do uruchamiania na *platformę docelową*, czyli konkretnej wersji programu .NET Framework i *platformę docelową*, czyli architektury konkretnego oprogramowania.  Można na przykład wskazać aplikację do uruchamiania na .NET Framework 2.0 na 32-bitowej platformie, która jest zgodna z rodziny procesorów 802 x 86 ("x86"). Kombinacja wartości docelowej i platforma docelowa jest znany jako *kontekstu docelowej*.  
  
## <a name="target-framework-and-profile"></a>Platforma docelowa i profilu  
 Platforma docelowa to konkretna wersja [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] przeznaczonego do uruchamiania na projekt. Określanie platformy docelowej jest wymagana, ponieważ umożliwia ona funkcje kompilatora i odwołania do zestawów, które należą wyłącznie do tej wersji w ramach.  
  
 Obecnie następujące wersje programu .NET Framework są dostępne do użycia:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 (zawarty w programie Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0 (zawarte w [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 (zawarte w [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (dołączone do programu Visual Studio 2010)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5 (zawarte w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1 (zawarte w [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6 (zawarte w [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)])  
  
  Na liście zestawów, że każdy sprawia, że można odwoływać się do wersji programu .NET Framework różnią się od siebie. Na przykład nie można tworzyć aplikacje Windows Presentation Foundation (WPF), chyba że projekt jest przeznaczony dla .NET Framework w wersji 3.0 lub nowszej.  
  
  Platforma docelowa jest określona w `TargetFrameworkVersion` właściwości w pliku projektu. Możesz zmienić platformę docelową dla projektu, używając strony właściwości projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE). Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostępne wartości dla `TargetFrameworkVersion` są `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2`, i `v4.6`.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *docelowy profil* to podzbiór platformy docelowej. Na przykład profilu klienta .NET Framework 4 nie zawiera odwołania do zestawów programu MSBuild.  
  
 Profil docelowy jest określona w `TargetFrameworkProfile` właściwości w pliku projektu. Profil docelowy można zmienić za pomocą formantu platformy docelowej na stronach właściwości projektu w środowisku IDE. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Platforma docelowa  
 A *platformy* jest kombinację sprzętu i oprogramowania, który definiuje konkretnego środowiska. Na przykład  
  
- `x86` Określa 32-bitowym systemie operacyjnym Windows działa na procesorze Intel 80 x 86 lub jego odpowiednika.  
  
- `Xbox` Określa platformę Microsoft Xbox 360.  
  
  A *platformę docelową* jest konkretnej platformie, że projekt został skompilowany do uruchamiania na. Platforma docelowa jest określona w `Platform` kompilacji właściwości w pliku projektu. Można zmienić platformę docelową, używając strony właściwości projektu lub **programu Configuration Manager** w środowisku IDE.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 A *konfiguracji docelowej* to podzbiór platformy docelowej. Na przykład `x86``Debug` konfiguracja nie obejmuje większość optymalizacji kodu. Konfiguracji docelowego jest określony w `Configuration` kompilacji właściwości w pliku projektu. Można zmienić konfiguracji docelowej, używając strony właściwości projektu lub **programu Configuration Manager**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)
