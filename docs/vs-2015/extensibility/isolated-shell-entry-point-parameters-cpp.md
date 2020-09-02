---
title: Parametry punktu wejścia izolowanej powłoki (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825159"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametry punktu wejścia w programie Shell (izolowanym) — C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy uruchamiana jest aplikacja oparta na programie Visual Studio Shell, wywołuje początkowy punkt wejścia powłoki programu Visual Studio. Następujące ustawienia mogą zostać zastąpione w wywołaniu punktu wejścia uruchomienia powłoki. Opis każdego ustawienia można znaleźć w temacie [. Pliki pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- Argumentu  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Szablon izolowany programu Visual Studio Shell tworzy plik źródłowy, *SolutionName*. cpp, gdzie *SolutionName* jest nazwą rozwiązania dla aplikacji. Ten plik definiuje główny punkt wejścia dla aplikacji, funkcję _tWinMain. Ta funkcja wywołuje początkowy punkt wejścia powłoki.  
  
  Zachowanie aplikacji można zmienić, zmieniając te ustawienia podczas uruchamiania aplikacji.  
  
## <a name="parameters"></a>Parametry  
 Początkowy punkt wejścia powłoki programu Visual Studio definiuje pięć parametrów. Nie należy zmieniać pierwszych czterech parametrów. Piąty parametr przyjmuje listę ustawień zastąpień. Początkowy punkt wejścia powłoki jest wywoływany z głównego punktu wejścia aplikacji.  
  
 Początkowy punkt wejścia powłoki ma następującą sygnaturę.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Jeśli nie chcesz przesłonić żadnych ustawień aplikacji, pozostaw wartość parametru ustawienia jako wskaźnik o wartości null.  
  
 Aby zastąpić jedno lub więcej ustawień, należy przekazać ciąg Unicode zawierający ustawienia, które mają zostać zastąpione. Ciąg jest rozdzielaną średnikami listą par nazwa-wartość. Każda para zawiera nazwę ustawienia do przesłonięcia, po którym następuje znak równości (=), a następnie wartość, która ma zostać zastosowana do ustawienia.  
  
> [!NOTE]
> W ciągach Unicode nie należy umieszczać białych znaków.  
  
 W przypadku ustawień logicznych następujące ciągi reprezentują wartość true; wszystkie inne ciągi reprezentują wartość false. W tych ciągach nie jest rozróżniana wielkość liter.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- tak  
  
## <a name="example"></a>Przykład  
 Aby wyłączyć dodatki i zmienić domyślną lokalizację projektów dla aplikacji, można ustawić ostatni parametr na "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie powłoki izolowanej](../extensibility/customizing-the-isolated-shell.md)   
 [Pliki .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
