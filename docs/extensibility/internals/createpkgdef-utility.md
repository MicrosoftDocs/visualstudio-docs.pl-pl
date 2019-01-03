---
title: Narzędzie CreatePkgDef | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5c18e77405cd4e48c89d3b481937c7d837488cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910938"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
Pobiera plik .dll dla rozszerzenia programu Visual Studio, jako parametr i tworzy *.pkgdef* pliku, który towarzyszy *.dll* pliku. *.Pkgdef* plik zawiera wszystkie informacje, które w przeciwnym razie powinny być zapisane w rejestrze systemu, gdy rozszerzenie jest zainstalowane.  
  
> [!NOTE]
>  Większość szablonów projektu, które są objęte zestawu SDK programu Visual Studio automatycznie utworzyć *.pkgdef* pliki jako część procesu kompilacji. Ten dokument jest przeznaczony dla osób, które chcesz ręcznie tworzyć pakiety lub konwertowania istniejących pakietów do użycia *.pkgdef* wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>  
```  
  
## <a name="arguments"></a>Argumenty  
 **/ out =&lt;nazwy pliku&gt;**  
 Wymagana. Ustawia nazwę *.pkgdef* plik wyjściowy będzie &lt;FileName&gt;.  
  
 **/ codebase**  
 Opcjonalna. Wymusza rejestrację przy użyciu **CodeBase** narzędzia.  
  
 **/ Assembly**  
 Wymusza rejestrację przy użyciu **zestawu** narzędzia.  
  
 **&lt;Ścieżkazestawu&gt;**  
 Ścieżka *.dll* pliku, z którego chcesz wygenerować *.pkgdef*.  
  
## <a name="remarks"></a>Uwagi  
 Rozwój rozszerzeń przy użyciu *.pkgdef* plików zastępuje wymagania rejestru wcześniejszych wersji programu Visual Studio.  
  
 *.Pkgdef* pliki muszą być zainstalowane w jednym z następujących lokalizacji: 

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\* 
 
- *%vsinstalldir%\Common7\IDE\Extensions\\*
    
  Jeśli folder instalacji to *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, rozszerzenie zostanie rozpoznane przez program Visual Studio, ale zostanie domyślnie wyłączona. Użytkownik może włączyć rozszerzenie za pomocą **rozszerzenia i aktualizacje**. 
   
  Jeśli folder instalacji to *%vsinstalldir%\Common7\IDE\Extensions\\*, rozszerzenie jest domyślnie włączona.  
  
> [!NOTE]
>  **Rozszerzenia i aktualizacje** narzędzie nie może służyć do dostępu do rozszerzenia, chyba, że jest zainstalowany jako część pakietu VSIX.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)