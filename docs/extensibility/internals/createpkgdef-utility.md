---
title: Narzędzie CreatePkgDef | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709167"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
Przyjmuje plik dll dla rozszerzenia programu Visual Studio jako parametr i tworzy plik *pkgdef,* który będzie towarzyszył plikowi *dll.* Plik *.pkgdef* zawiera wszystkie informacje, które w przeciwnym razie zostałyby zapisane w rejestrze systemowym po zainstalowaniu rozszerzenia.

> [!NOTE]
> Większość szablonów projektu, które są zawarte w visual studio SDK automatycznie utworzyć pliki *pkgdef* jako część procesu kompilacji. Ten dokument jest przeznaczony dla tych, którzy chcą ręcznie tworzyć pakiety lub konwertować istniejące pakiety do użycia wdrożenia *pkgdef.*

## <a name="syntax"></a>Składnia

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumenty
**/out=&lt;Nazwa pliku&gt;**\
Wymagany. Ustawia nazwę pliku wyjściowego *pkgdef* na &lt;&gt;FileName .

**/codebase**\
Element opcjonalny. Wymusza rejestrację za pomocą narzędzia **CodeBase.**

**/montaż**\
Wymusza rejestrację za pomocą narzędzia **Assembly.**

**&lt;Ścieżka zespołu&gt;**\
Ścieżka pliku *dll,* z którego ma zostać wygenerowana *pkgdef*.

## <a name="remarks"></a>Uwagi
Wdrożenie rozszerzenia przy użyciu plików *pkgdef* zastępuje wymagania rejestru wcześniejszych wersji programu Visual Studio.

::: moniker range=">=vs-2019"

Pliki *.pkgdef* muszą być zainstalowane w jednej z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\16.0\Rozszerzenia\\*

- *%vsinstalldir%\Common7\IDE\Rozszerzenia\\*

Jeśli folder instalacyjny to *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*, rozszerzenie jest rozpoznawane przez program Visual Studio, ale jest domyślnie wyłączone. Użytkownik może włączyć rozszerzenie za pomocą **funkcji Zarządzaj rozszerzeniami**.

Jeśli folder instalacyjny to *%vsinstalldir%\Common7\IDE\Extensions\\*, rozszerzenie jest domyślnie włączone.

> [!NOTE]
> Narzędzia **Zarządzaj rozszerzeniami** nie można użyć do uzyskania dostępu do rozszerzenia, chyba że jest ono zainstalowane jako część pakietu VSIX.

::: moniker-end

::: moniker range="vs-2017"

Pliki *.pkgdef* muszą być zainstalowane w jednej z następujących lokalizacji:

- *%localappdata%\Microsoft\Visual Studio\15.0\Rozszerzenia\\*

- *%vsinstalldir%\Common7\IDE\Rozszerzenia\\*

Jeśli folder instalacyjny to *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*, rozszerzenie jest rozpoznawane przez program Visual Studio, ale jest domyślnie wyłączone. Użytkownik może włączyć rozszerzenie za pomocą **rozszerzeń i aktualizacji**.

Jeśli folder instalacyjny to *%vsinstalldir%\Common7\IDE\Extensions\\*, rozszerzenie jest domyślnie włączone.

> [!NOTE]
> Narzędzia **Rozszerzenia i aktualizacje** nie można użyć do uzyskania dostępu do rozszerzenia, chyba że jest ono zainstalowane jako część pakietu VSIX.

::: moniker-end

## <a name="see-also"></a>Zobacz też
- [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
