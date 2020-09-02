---
title: Narzędzie CreatePkgDef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782985"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przyjmuje plik. dll rozszerzenia programu Visual Studio jako parametr i tworzy plik. pkgdef, który towarzyszy bibliotece DLL. Plik. pkgdef zawiera wszystkie informacje, które w przeciwnym razie byłyby zapisywane w rejestrze systemowym, gdy rozszerzenie zostanie zainstalowane.  
  
> [!NOTE]
> Większość szablonów projektu, które są zawarte w zestawie SDK programu Visual Studio, automatycznie tworzy pliki pkgdef jako część procesu kompilacji. Ten dokument jest przeznaczony dla użytkowników, którzy chcą ręcznie tworzyć pakiety, lub konwertować istniejące pakiety do użycia. pkgdef.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumenty  
 /out =`FileName`  
 Wymagany. Ustawia nazwę pliku wyjściowego. pkgdef na `FileName` .  
  
 /codebase  
 Opcjonalny. Wymusza rejestrację za pomocą narzędzia CodeBase.  
  
 /Assembly  
 Wymusza rejestrację za pomocą narzędzia zestawu.  
  
 `AssemblyPath`  
 Ścieżka do pliku dll, z którego chcesz wygenerować plik. pkgdef.  
  
## <a name="remarks"></a>Uwagi  
 Wdrożenie rozszerzenia przy użyciu plików. pkgdef zastępuje wymagania dotyczące rejestru wcześniejszych wersji programu Visual Studio.  
  
 Pliki. pkgdef muszą być zainstalowane w jednej z następujących lokalizacji:%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ lub%vsinstalldir%\Common7\IDE\Extensions \\ . Jeśli folder instalacji to%localappdata%\Microsoft\Visual Studio\14.0\Extensions \\ , rozszerzenie zostanie rozpoznane przez program Visual Studio, ale zostanie domyślnie wyłączone. Użytkownik może włączyć rozszerzenie przy użyciu **rozszerzeń i aktualizacji**. Jeśli folder instalacyjny to%vsinstalldir%\Common7\IDE\Extensions \\ , rozszerzenie jest domyślnie włączone.  
  
> [!NOTE]
> Narzędzia **rozszerzenia i aktualizacje** nie można użyć w celu uzyskania dostępu do rozszerzenia, chyba że zostanie ono zainstalowane jako część pakietu VSIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
