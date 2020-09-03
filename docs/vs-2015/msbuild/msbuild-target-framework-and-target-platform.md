---
title: Struktura docelowa programu MSBuild i platforma docelowa | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181019"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Platforma docelowa programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekt można skompilować do uruchamiania w *środowisku docelowym*, który jest określoną wersją .NET Framework i *platformą docelową*, która jest konkretną architekturą oprogramowania.  Można na przykład określić, że aplikacja ma być uruchamiana na .NET Framework 2,0 na platformie 32-bitowej, która jest zgodna z rodziną procesorów 802x86 ("x86"). Kombinacja struktury docelowej i platformy docelowej jest znana jako *kontekst docelowy*.  
  
## <a name="target-framework-and-profile"></a>Struktura docelowa i profil  
 Platforma docelowa to określona wersja [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , w której ma zostać uruchomiony projekt. Specyfikacja platformy docelowej jest wymagana, ponieważ włącza funkcje kompilatora i odwołania do zestawów, które są wyłącznie dla tej wersji platformy.  
  
 Obecnie następujące wersje .NET Framework są dostępne do użycia:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2,0 (zawarte w Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]3,0 (uwzględnione w [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]3,5 (uwzględnione w [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4 (zawarte w Visual Studio 2010)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4,5 (uwzględnione w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.1 (dołączone do [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4,6 (uwzględnione w [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] )  
  
  Wersje .NET Framework różnią się od siebie na liście zestawów, które każda z nich udostępnia. Na przykład nie można kompilować aplikacji Windows Presentation Foundation (WPF), chyba że projekt jest przeznaczony dla .NET Framework w wersji 3,0 lub nowszej.  
  
  Struktura docelowa jest określona we `TargetFrameworkVersion` właściwości w pliku projektu. Można zmienić platformę docelową dla projektu przy użyciu stron właściwości projektu w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostępne wartości to,,,,,, `TargetFrameworkVersion` `v2.0` `v3.0` `v3.5` `v4.0` `v4.5` `v4.5.1` `v4.5.2` i `v4.6` .  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *Profil docelowy* jest podzbiorem platformy docelowej. Na przykład profil klienta .NET Framework 4 nie zawiera odwołań do zestawów programu MSBuild.  
  
 Profil docelowy jest określony we `TargetFrameworkProfile` właściwości w pliku projektu. Profil docelowy można zmienić przy użyciu formantu Target-Framework na stronach właściwości projektu w IDE. Aby uzyskać więcej informacji, zobacz [How to: Target of a wersja .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Platforma docelowa  
 *Platformą* jest kombinacja sprzętu i oprogramowania, która definiuje określone środowisko uruchomieniowe. Przykład:  
  
- `x86` Określa 32-bitowy system operacyjny Windows, który działa na procesorze Intel 80x86 lub jego odpowiedniku.  
  
- `Xbox` wyznacza platformę Microsoft Xbox 360.  
  
  *Platforma docelowa* to określona platforma, na której ma być uruchamiany projekt. Platforma docelowa jest określona we `Platform` Właściwości kompilacja w pliku projektu. Możesz zmienić platformę docelową, korzystając ze stron właściwości projektu lub **Configuration Manager** w IDE.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *Konfiguracja docelowa* jest podzbiorem platformy docelowej. Na przykład `x86``Debug` Konfiguracja nie obejmuje większości optymalizacji kodu. Konfiguracja docelowa jest określona we `Configuration` Właściwości kompilacja w pliku projektu. Konfigurację docelową można zmienić przy użyciu stron właściwości projektu lub **Configuration Manager**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowersyjności kodu](../msbuild/msbuild-multitargeting-overview.md)
