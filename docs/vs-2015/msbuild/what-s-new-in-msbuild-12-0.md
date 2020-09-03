---
title: Co&#39;s w programie MSBuild 12,0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba733b7ef20c9a03ad19d9847a4046e4d72ebdef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844453"
---
# <a name="what39s-new-in-msbuild-120"></a>Co&#39;s Nowość w programie MSBuild 12,0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program MSBuild jest teraz instalowany jako część programu Visual Studio, a nie jako część .NET Framework. Bieżący numer wersji programu MSBuild to 12,0. Jeśli chcesz zainstalować program MSBuild oddzielnie, Pobierz pakiet instalacyjny z programu [MSBuild Download](https://www.microsoft.com/download/details.aspx?id=40760).  
  
## <a name="changed-path"></a>Zmieniona ścieżka  
 Program MSBuild jest teraz instalowany bezpośrednio w folderze *% ProgramFiles%*— na przykład w lokalizacji C:\Program Files\MSBuild \\ .  
  
## <a name="changed-properties"></a>Zmienione właściwości  
 Następujące właściwości programu MSBuild są zmieniane w wyniku nowego numeru wersji:  
  
- `MSBuildToolsVersion` w przypadku tej wersji narzędzi jest 12,0.  
  
- `MSBuildToolsPath` teraz%ProgramFiles%\MSBuild\12.0\bin 32-bitowe systemy operacyjne lub%ProgramFiles%\MSBuild\12.0\bin\amd64 w systemach operacyjnych 64-bitowych.  
  
- `ToolsVersion` wartości można znaleźć w HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 dla 32-bitowych systemów operacyjnych lub HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 dla systemów operacyjnych 64-bitowych.  
  
- `SDK35ToolsPath`Właściwości i `SDK40ToolsPath` wskazują zestawowi .NET Framework SDK, który jest spakowany z tą wersją programu Visual Studio (na przykład 8.1 a dla narzędzi 4. X).  
  
## <a name="new-properties"></a>Nowe właściwości  
  
- `MSBuildFrameworkToolsPath` to nowa właściwość, która ma wartość%windir%\Microsoft.NET\Framework\v4.0.30319 w 32-bitowych systemach operacyjnych lub%windir%\Microsoft.NET\Framework64\v4.0.30319 w systemach operacyjnych 64-bitowych. Jest to zamiennik dla programu `MSBuildToolsPath` , którego można użyć, aby wskazać narzędzia .NET Framework i narzędzi.  
  
- `MSBuildToolsPath` i `MSBuildFrameworkToolsPath` mają 32-bitowe odpowiedniki — `MSBuildToolsPath32` i `MSBuildFrameworkToolsPath32` — które zawsze wskazują na lokalizację 32-bitową, niezależnie od tego, czy jest używany program MSBuild 32-bit czy 64-bit.

## <a name="see-also"></a>Zobacz też
[MSBuild](msbuild.md)
