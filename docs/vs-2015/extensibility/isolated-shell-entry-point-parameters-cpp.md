---
title: Izolowany Parametry punktu wejścia powłoki (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 270a5c932429a518447d0029b05d3c9522db7387
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749175"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametry punktu wejścia Isolated Shell (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po uruchomieniu aplikacji opartych na powłoce Visual Studio wywołuje punkt wejścia uruchamiania powłoki programu Visual Studio. Następujące ustawienia można zastąpić w wywołaniu do punktu wejścia uruchamiania powłoki. Aby uzyskać opis każdego ustawienia, zobacz [. Pliki Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
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
  
  Visual Studio Shell izolowane szablon tworzy plik źródłowy *solutionName*.cpp, gdzie *solutionName* jest nazwą rozwiązania dla aplikacji. Ten plik definiuje główny punkt wejścia dla aplikacji funkcji _tWinMain. Ta funkcja wywołuje punkt wejścia początkowy powłoki.  
  
  Sposób działania aplikacji można zmienić, zmieniając tych ustawień podczas uruchamiania aplikacji.  
  
## <a name="parameters"></a>Parametry  
 Punkt wejścia uruchamiania powłoki programu Visual Studio definiuje pięć parametrów. Nie zmieniaj pierwsze cztery parametry. Piąty parametr przyjmuje listę zastąpienie ustawień. Punkt wejścia początkowy powłoki jest wywoływana z główny punkt wejścia aplikacji.  
  
 Punkt wejścia początkowy powłoki ma następujący podpis.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Jeśli nie chcesz zastąpić wszelkie ustawienia aplikacji, pozostaw wartość ustawienia zastępowania parametru jako wskaźnikiem typu null.  
  
 Aby zastąpić co najmniej jedno ustawienie, należy przekazać ciąg Unicode, który zawiera ustawienia do zastąpienia. Ten ciąg jest rozdzieloną średnikami listę par nazwa wartość. Każda para zawiera nazwę ustawienie, aby zastąpić, następuje znak równości (=), a następnie według wartości, aby zastosować ustawienia.  
  
> [!NOTE]
>  Nie dołączaj białe znaki w ciągach znaków Unicode.  
  
 Wartość logiczna ustawień następujące ciągi reprezentować wartość true; inne ciągi reprezentować wartość false. Tych ciągów jest rozróżniana wielkość liter.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   on  
  
-   true  
  
-   Tak  
  
## <a name="example"></a>Przykład  
 Aby wyłączyć dodatki i zmiany domyślnej lokalizacji projektów aplikacji, można ustawić ostatni parametr "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md)   
 [Pliki pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

