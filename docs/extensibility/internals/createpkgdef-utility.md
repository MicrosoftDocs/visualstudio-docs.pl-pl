---
title: CreatePkgDef Utility | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5866949d6ccfa9f3b1037abf7801ce40ace3d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332283"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
Pobiera plik .dll dla rozszerzenia programu Visual Studio, jako parametr i tworzy *.pkgdef* pliku, który towarzyszy *.dll* pliku. *.Pkgdef* plik zawiera wszystkie informacje, które w przeciwnym razie powinny być zapisane w rejestrze systemu, gdy rozszerzenie jest zainstalowane.

> [!NOTE]
> Większość szablonów projektu, które są objęte zestawu SDK programu Visual Studio automatycznie utworzyć *.pkgdef* pliki jako część procesu kompilacji. Ten dokument jest przeznaczony dla osób, które chcesz ręcznie tworzyć pakiety lub konwertowania istniejących pakietów do użycia *.pkgdef* wdrożenia.

## <a name="syntax"></a>Składnia

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumenty
**/out=&lt;FileName&gt;** \
Wymagana. Ustawia nazwę *.pkgdef* plik wyjściowy będzie &lt;FileName&gt;.

**/ codebase**\
Opcjonalna. Wymusza rejestrację przy użyciu **CodeBase** narzędzia.

**/ Assembly**\
Wymusza rejestrację przy użyciu **zestawu** narzędzia.

**&lt;AssemblyPath&gt;** \
Ścieżka *.dll* pliku, z którego chcesz wygenerować *.pkgdef*.

## <a name="remarks"></a>Uwagi
Rozwój rozszerzeń przy użyciu *.pkgdef* plików zastępuje wymagania rejestru wcześniejszych wersji programu Visual Studio.

::: moniker range=">=vs-2019"

*.Pkgdef* pliki muszą być zainstalowane w jednym z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Jeśli folder instalacji to *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\* , rozszerzenie jest rozpoznawany przez program Visual Studio, ale jest domyślnie wyłączona. Użytkownik może włączyć rozszerzenie za pomocą **Zarządzaj rozszerzeniami**.

Jeśli folder instalacji to *%vsinstalldir%\Common7\IDE\Extensions\\* , rozszerzenie jest domyślnie włączona.

> [!NOTE]
> **Zarządzaj rozszerzeniami** narzędzie nie może służyć do dostępu do rozszerzenia, chyba, że jest zainstalowany jako część pakietu VSIX.

::: moniker-end

::: moniker range="vs-2017"

*.Pkgdef* pliki muszą być zainstalowane w jednym z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Jeśli folder instalacji to *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\* , rozszerzenie jest rozpoznawany przez program Visual Studio, ale jest domyślnie wyłączona. Użytkownik może włączyć rozszerzenie za pomocą **rozszerzenia i aktualizacje**.

Jeśli folder instalacji to *%vsinstalldir%\Common7\IDE\Extensions\\* , rozszerzenie jest domyślnie włączona.

> [!NOTE]
> **Rozszerzenia i aktualizacje** narzędzie nie może służyć do dostępu do rozszerzenia, chyba, że jest zainstalowany jako część pakietu VSIX.

::: moniker-end

## <a name="see-also"></a>Zobacz także
- [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
