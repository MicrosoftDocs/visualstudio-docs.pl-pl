---
title: Platforma docelowa programu MSBuild i platformy docelowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3248fea80c2afe4ec2874bce381dda105ddd6ae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825616"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Program MSBuild docelowej platformy framework i docelowego
Można skompilować projekt, do uruchamiania na *platformę docelową*, czyli konkretnej wersji programu .NET Framework i *platformę docelową*, czyli architektury konkretnego oprogramowania.  Można na przykład wskazać aplikację do uruchamiania na .NET Framework 2.0 na 32-bitowej platformie, która jest zgodna z rodziny procesorów 802 x 86 ("x86"). Kombinacja wartości docelowej i platforma docelowa jest znany jako *kontekstu docelowej*.  
  
## <a name="target-framework-and-profile"></a>Platforma docelowa i profilu  
 Platforma docelowa to konkretna wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] przeznaczonego do uruchamiania na projekt. Określanie platformy docelowej jest wymagana, ponieważ umożliwia ona funkcje kompilatora i odwołania do zestawów, które należą wyłącznie do tej wersji w ramach.  
  
 Obecnie następujące wersje programu .NET Framework są dostępne do użycia:  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (zawarty w programie Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (zawarte w [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (zawarte w [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (zawarte w [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  

Na liście zestawów, że każdy sprawia, że można odwoływać się do wersji programu .NET Framework różnią się od siebie. Na przykład nie można tworzyć aplikacje Windows Presentation Foundation (WPF), chyba że projekt jest przeznaczony dla .NET Framework w wersji 3.0 lub nowszej.  

Platforma docelowa jest określona w `TargetFrameworkVersion` właściwości w pliku projektu. Możesz zmienić platformę docelową dla projektu, używając strony właściwości projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE). Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostępne wartości dla `TargetFrameworkVersion` są `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, i `v4.7.1`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *docelowy profil* to podzbiór platformy docelowej. Na przykład profilu klienta .NET Framework 4 nie zawiera odwołania do zestawów programu MSBuild.  
  
 Profil docelowy jest określona w `TargetFrameworkProfile` właściwości w pliku projektu. Profil docelowy można zmienić za pomocą formantu platformy docelowej na stronach właściwości projektu w środowisku IDE. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Platforma docelowa  
 A *platformy* jest kombinację sprzętu i oprogramowania, który definiuje konkretnego środowiska. Na przykład  
  
-   `x86` Określa 32-bitowym systemie operacyjnym Windows działa na procesorze Intel 80 x 86 lub jego odpowiednika.  

-   `x64` Określa w systemie operacyjnym Windows 64-bitowym, który działa na procesorze Intel x64 lub równoważnej.
  
-   `Xbox` Określa platformę Microsoft Xbox 360.  

A *platformę docelową* jest konkretnej platformie, że projekt został skompilowany do uruchamiania na. Platforma docelowa jest określona w `PlatformTarget` kompilacji właściwości w pliku projektu. Można zmienić platformę docelową, używając strony właściwości projektu lub **programu Configuration Manager** w środowisku IDE.  

```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
</PropertyGroup>  

```  

A *konfiguracji docelowej* to podzbiór platformy docelowej. Na przykład `x86``Debug` konfiguracja nie obejmuje większość optymalizacji kodu. Konfiguracji docelowego jest określony w `Configuration` kompilacji właściwości w pliku projektu. Można zmienić konfiguracji docelowej, używając strony właściwości projektu lub **programu Configuration Manager**.  

```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  

## <a name="see-also"></a>Zobacz także  
 [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)
