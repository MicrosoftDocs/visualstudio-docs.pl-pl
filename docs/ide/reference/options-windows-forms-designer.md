---
title: Opcje, Projektant formularzy systemu Windows, Ogólne
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2a72b27dc2277501d0e0957c8b89b551f4d6852d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568064"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Okno dialogowe Opcje: Projektant formularzy systemu Windows

Strona opcji Projektanta formularzy systemu Windows umożliwia ustawienie preferencji dla siatek i innych funkcji projektanta formularzy systemu Windows w programie Visual Studio. Otwórz okno dialogowe **Opcje** z menu **Narzędzia.**

## <a name="code-generation-settings"></a>Ustawienia generowania kodu

**Zoptymalizowana generacja kodu**\
Umożliwia generowanie zoptymalizowanych kodów. Niektóre elementy sterujące mogą nie być zgodne z tym trybem. Aby ta zmiana została wniesienia w życie, visual studio musi zostać zamknięty i ponownie otwarty.

## <a name="high-dpi-support"></a>Obsługa wysokiej rozdzielczości DPI

**Powiadomienia o skalowaniu DPI**\
Pokaż komunikat w projektancie formularzy systemu Windows, który można ponownie uruchomić program Visual Studio z 100% skalowania. Aby uzyskać więcej informacji, zobacz [Wyłączanie dpi-awareness w programie Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Ustawienia układu

**Domyślny rozmiar komórki siatki**\
Ustawia odstępy między poziomymi i pionowymi liniami siatki w projektancie. Domyślny rozmiar to 8, 8. Maksymalny rozmiar to 200, 200.

**Tryb układu**\
Określa system wyrównania, który ma być używany dla układu. Można wybrać snaptogrid lub snaplines.

**Pokaż siatkę**\
Określa, czy projektanci wyświetlają siatkę zmiany rozmiaru. Domyślnie siatka jest włączona.

**Przyciąganie do siatki**\
Określa, czy projektanci będą przyciągać obiekty i formanty do siatki. Innymi słowy, zmiana rozmiaru i ruch elementów na projektancie są ograniczone do przyrostu GridSize, gdy ta funkcja jest włączona. Po snaptogrid włączony ułatwia ujednuć różne aspekty interfejsu użytkownika dokładnie, ale ogranicza swobodę, z jaką można umieścić kontroli. Domyślnie SnapToGrid jest włączona.

## <a name="object-bound-smart-tag-settings"></a>Ustawienia tagów inteligentnych powiązanych z obiektem

**Automatyczne otwieranie tagów inteligentnych**\
Określa, czy formanty i składniki wyświetlają tagi inteligentne. Nie wszystkie formanty i składniki obsługują tagi inteligentne.

## <a name="refactoring"></a>Refaktoryzacja

**Włącz refaktoryzowanie przy zmianie nazwy**\
Po ustawieniu `true`operacji refaktoryzacji zmiany nazwy jest wykonywana po zmianie nazwy składnika z okna Właściwości lub Konspektu dokumentu.

## <a name="toolbox"></a>Przybornik

**Automatyczne wypełnianie przybornika**\
Określa, czy okno przybornika jest automatycznie wypełniane komponentami i formantami zbudowanymi przez projekt.
