---
title: Narzędzie CreatePkgDef | Microsoft Docs
description: Dowiedz się więcej o narzędziu CreatePkgDef, które pobiera plik .dll dla rozszerzenia Visual Studio jako parametr i tworzy plik pkgdef towarzyszący plikowi .dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfbd4b42d9ceddd40e08c28926a59aecba719fe9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898126"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
Pobiera plik .dll dla rozszerzenia Visual Studio jako parametr i tworzy *plik pkgdef,* który ma towarzyszyć.dll *pliku.* Plik *.pkgdef* zawiera wszystkie informacje, które w przeciwnym razie zostałyby zapisane w rejestrze systemowym po zainstalowaniu rozszerzenia.

> [!NOTE]
> Większość szablonów projektów uwzględnionych w zestawie SDK Visual Studio automatycznie tworzy pliki *pkgdef* w ramach procesu kompilacji. Ten dokument jest przeznaczony dla osób, które chcą ręcznie tworzyć pakiety lub konwertować istniejące pakiety na wdrożenie *pkgdef.*

## <a name="syntax"></a>Składnia

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumenty
**/out = &lt; Nazwa pliku&gt;**\
Wymagane. Ustawia nazwę pliku *wyjściowego pkgdef* na &lt; FileName &gt; .

**/codebase**\
Opcjonalny. Wymusza rejestrację za pomocą **narzędzia CodeBase.**

**/assembly**\
Wymusza rejestrację za pomocą **narzędzia Assembly.**

**&lt;AssemblyPath&gt;**\
Ścieżka pliku *.dll,* z którego chcesz wygenerować *plik pkgdef.*

## <a name="remarks"></a>Uwagi
Wdrożenie rozszerzenia przy użyciu *plików pkgdef* zastępuje wymagania rejestru wcześniejszych wersji Visual Studio.

::: moniker range=">=vs-2019"

Pliki *pkgdef* muszą być zainstalowane w jednej z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Jeśli folder instalacji to *%localappdata%\Microsoft\Visual Studio\16.0\Extensions, \\* rozszerzenie jest rozpoznawane przez program Visual Studio ale jest domyślnie wyłączone. Użytkownik może włączyć rozszerzenie przy użyciu **funkcji Zarządzaj rozszerzeniami**.

Jeśli folder instalacji to *%vsinstalldir%\Common7\IDE\Extensions, \\* rozszerzenie jest domyślnie włączone.

> [!NOTE]
> Narzędzia **Do zarządzania rozszerzeniami** nie można używać do uzyskiwania dostępu do rozszerzenia, chyba że jest ono zainstalowane jako część pakietu VSIX.

::: moniker-end

::: moniker range="vs-2017"

Pliki *pkgdef* muszą być zainstalowane w jednej z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Jeśli folder instalacji to *%localappdata%\Microsoft\Visual Studio\15.0\Extensions, \\* rozszerzenie jest rozpoznawane przez program Visual Studio ale jest domyślnie wyłączone. Użytkownik może włączyć rozszerzenie przy użyciu **rozszerzenia i aktualizacji**.

Jeśli folder instalacji to *%vsinstalldir%\Common7\IDE\Extensions, \\* rozszerzenie jest domyślnie włączone.

> [!NOTE]
> Narzędzia **Rozszerzenia i aktualizacje** nie można używać do uzyskiwania dostępu do rozszerzenia, chyba że jest ono zainstalowane jako część pakietu VSIX.

::: moniker-end

## <a name="see-also"></a>Zobacz też
- [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
