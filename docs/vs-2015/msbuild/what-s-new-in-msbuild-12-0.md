---
title: Co&#39;nowego w programie MSBuild 12,0 | Microsoft Docs
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844453"
---
# <a name="what39s-new-in-msbuild-120"></a>Co&#39;nowego w programie MSBuild 12,0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program MSBuild jest teraz instalowany jako część programu Visual Studio, a nie jako część .NET Framework. Bieżący numer wersji programu MSBuild to 12,0. Jeśli chcesz zainstalować program MSBuild oddzielnie, Pobierz pakiet instalacyjny z programu [MSBuild Download](https://www.microsoft.com/download/details.aspx?id=40760).  
  
## <a name="changed-path"></a>Zmieniona ścieżka  
 Program MSBuild jest teraz instalowany bezpośrednio w folderze *% ProgramFiles%* — na przykład w folderze C:\Program Files\MSBuild\\.  
  
## <a name="changed-properties"></a>Zmienione właściwości  
 Następujące właściwości programu MSBuild są zmieniane w wyniku nowego numeru wersji:  
  
- `MSBuildToolsVersion` tej wersji narzędzi to 12,0.  
  
- `MSBuildToolsPath` jest teraz%ProgramFiles%\MSBuild\12.0\bin w 32-bitowych systemach operacyjnych lub%ProgramFiles%\MSBuild\12.0\bin\amd64 w systemach operacyjnych 64-bitowych.  
  
- wartości `ToolsVersion` można znaleźć w HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 dla 32-bitowych systemów operacyjnych lub HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 dla systemów operacyjnych 64-bitowych.  
  
- Właściwości `SDK35ToolsPath` i `SDK40ToolsPath` wskazują zestaw .NET Framework SDK, który jest opakowany z tą wersją programu Visual Studio (na przykład 8.1 A dla narzędzi 4. X).  
  
## <a name="new-properties"></a>Nowe właściwości  
  
- `MSBuildFrameworkToolsPath` to nowa właściwość, która ma wartość%windir%\Microsoft.NET\Framework\v4.0.30319 w 32-bitowych systemach operacyjnych lub%windir%\Microsoft.NET\Framework64\v4.0.30319 w systemach operacyjnych 64-bitowych. Jest to zamiennik dla `MSBuildToolsPath`, którego można użyć do wskazywania .NET Framework narzędzi i narzędzi.  
  
- `MSBuildToolsPath` i `MSBuildFrameworkToolsPath` posiadają 32-bitowe odpowiedniki —`MSBuildToolsPath32` i `MSBuildFrameworkToolsPath32`— które zawsze wskazują na lokalizację 32-bitową, niezależnie od tego, czy jest używany program MSBuild 32-bit czy 64-bit.

## <a name="see-also"></a>Zobacz też
[MSBuild](msbuild.md)
