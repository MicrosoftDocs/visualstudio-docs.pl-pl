---
title: Co&#39;s Nowość w programie MSBuild 12.0 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 324ea1e0409ea08b7580d9a6375e7ad96a539a92
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793974"
---
# <a name="what39s-new-in-msbuild-120"></a>Co&#39;s Nowość w programie MSBuild 12.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program MSBuild jest teraz zainstalowany jako część pakietu Visual Studio, a nie jako część programu .NET Framework. Bieżący numer wersji MSBuild to 12.0. Jeśli chcesz zainstalować program MSBuild oddzielnie, Pobierz pakiet instalacyjny z [Pobierz MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  
  
## <a name="changed-path"></a>Zmieniona ścieżka  
 Program MSBuild jest teraz zainstalowany bezpośrednio pod *% ProgramFiles %*— na przykład w C:\Program Files\MSBuild\\.  
  
## <a name="changed-properties"></a>Zmienionymi właściwościami  
 Następujące właściwości programu MSBuild zostały zmienione w wyniku nowy numer wersji:  
  
-   `MSBuildToolsVersion` dla tej wersji narzędzi to 12.0.  
  
-   `MSBuildToolsPath` jest teraz %ProgramFiles%\MSBuild\12.0\bin na 32-bitowych systemach operacyjnych lub %ProgramFiles%\MSBuild\12.0\bin\amd64 na 64-bitowych systemach operacyjnych.  
  
-   `ToolsVersion` wartości można znaleźć w HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 dla 32-bitowych systemach operacyjnych lub HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 dla 64-bitowych systemach operacyjnych.  
  
-   `SDK35ToolsPath` i `SDK40ToolsPath` właściwości wskaż .NET Framework SDK, który jest spakowany w tej wersji programu Visual Studio (na przykład 8.1a narzędzi 4.X).  
  
## <a name="new-properties"></a>Nowe właściwości  
  
-   `MSBuildFrameworkToolsPath` jest nową właściwość, która ma wartość %windir%\Microsoft.NET\Framework\v4.0.30319 na 32-bitowych systemach operacyjnych lub %windir%\Microsoft.NET\Framework64\v4.0.30319 na 64-bitowych systemach operacyjnych. Jest to zastępuje `MSBuildToolsPath` można wskaż opcję Narzędzia programu .NET Framework i programy narzędziowe.  
  
-   `MSBuildToolsPath` i `MSBuildFrameworkToolsPath` mają 32-bitowe odpowiedniki —`MSBuildToolsPath32` i `MSBuildFrameworkToolsPath32`— zawsze wskazujące na lokalizację 32-bitowych, niezależnie od tego, czy jest używana 32-bitową lub 64-bitowy MSBuild.

## <a name="see-also"></a>Zobacz też
[MSBuild](msbuild.md)
