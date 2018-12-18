---
title: Narzędzie CreatePkgDef | Dokumentacja firmy Microsoft
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
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 492e34c92019de7f3c0921b853d103252e09b996
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782651"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera plik .dll dla rozszerzenia programu Visual Studio, jako parametr i tworzy plik .pkgdef, która ma towarzyszyć plik .dll. Plik .pkgdef zawiera wszystkie informacje, które w przeciwnym razie powinny być zapisane w rejestrze systemu, gdy rozszerzenie jest zainstalowane.  
  
> [!NOTE]
>  Większość szablonów projektu, które są objęte zestawu SDK programu Visual Studio automatycznie tworzą pliki .pkgdef jako część procesu kompilacji. Ten dokument jest przeznaczony dla osób, które chcesz ręcznie tworzyć pakiety lub konwertowania istniejących pakietów przy użyciu wdrażania .pkgdef.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumenty  
 / out =`FileName`  
 Wymagana. Ustawia nazwę pliku wyjściowego .pkgdef do`FileName`.  
  
 /codebase  
 Opcjonalna. Wymusza rejestrację za pomocą narzędzia bazy kodu.  
  
 / Assembly  
 Wymusza rejestrację za pomocą narzędzia zestawu.  
  
 `AssemblyPath`  
 Ścieżka pliku dll, z którego chcesz wygenerować .pkgdef.  
  
## <a name="remarks"></a>Uwagi  
 Rozwój rozszerzeń przy użyciu plików .pkgdef zastępuje wymagania rejestru wcześniejszych wersji programu Visual Studio.  
  
 Pliki .pkgdef muszą być zainstalowane w jednym z następujących lokalizacji: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ lub %vsinstalldir%\Common7\IDE\Extensions\\. Jeśli folder instalacji to %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, rozszerzenie zostanie rozpoznane przez program Visual Studio, ale zostanie domyślnie wyłączona. Użytkownik może włączyć rozszerzenie za pomocą **rozszerzenia i aktualizacje**. Jeśli folder instalacji to %vsinstalldir%\Common7\IDE\Extensions\\, rozszerzenie jest domyślnie włączona.  
  
> [!NOTE]
>  **Rozszerzenia i aktualizacje** narzędzie nie może służyć do dostępu do rozszerzenia, chyba, że jest zainstalowany jako część pakietu VSIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

