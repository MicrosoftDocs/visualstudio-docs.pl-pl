---
title: Opcje, Projektant formularzy systemu Windows, ogólne
description: Dowiedz się, jak używać strony Ogólne do ustawiania preferencji dla siatek i innych funkcji Projektant formularzy systemu Windows w programie Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d7172ca12344ab046c9bf65e7df280a9fa6dd0aa
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040085"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Opcje — okno dialogowe: Projektant formularzy systemu Windows

Strona Opcje Projektant formularzy systemu Windows umożliwia ustawianie preferencji dla siatek i innych funkcji Projektant formularzy systemu Windows w programie Visual Studio. Otwórz okno dialogowe **Opcje** z menu **Narzędzia** .

## <a name="code-generation-settings"></a>Ustawienia generowania kodu

**Zoptymalizowane generowanie kodu**\
Włącza zoptymalizowane generowanie kodu. Niektóre kontrolki mogą nie być zgodne z tym trybem. Aby ta zmiana zaczęła obowiązywać, program Visual Studio musi być zamknięty i ponownie otwarty.

## <a name="high-dpi-support"></a>Obsługa wysokiej rozdzielczości DPI

**Powiadomienia skalowania DPI**\
Pokaż komunikat w projektancie formularzy systemu Windows, który może ponownie uruchomić program Visual Studio z skalowaniem do 100%. Aby uzyskać więcej informacji, zobacz [wyłączanie rozpoznawania dpi w programie Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Ustawienia układu

**Domyślny rozmiar komórki siatki**\
Ustawia odstępy (w pikselach) między poziomymi i pionowymi liniami siatki w projektancie. Domyślny rozmiar to 8, 8. Maksymalny rozmiar to 200, 200.

**Tryb układu**\
Określa system wyrównania, który ma być używany na potrzeby układu. Można wybrać opcję SnapToGrid lub linii wyrównania.

**Pokaż siatkę**\
Określa, czy projektanci mają wyświetlać siatkę wielkości. Domyślnie siatka jest włączona.

**Przyciągaj do siatki**\
Określa, czy projektanci będą przyciągać obiekty i kontrolki do siatki. Innymi słowy, zmiany rozmiarów i przenoszenia elementów projektanta są ograniczone do przyrostu GridSize, gdy ta funkcja jest włączona. Włączenie SnapToGrid ułatwia precyzyjne rozróżnienie różnych aspektów interfejsu użytkownika, ale ogranicza swobodę, z którą może umieścić formanty. Domyślnie SnapToGrid jest włączona.

## <a name="object-bound-smart-tag-settings"></a>Ustawienia tagów inteligentnych powiązane z obiektem

**Automatycznie otwieraj Tagi inteligentne**\
Określa, czy formanty i składniki wyświetlają Tagi inteligentne. Nie wszystkie formanty i składniki obsługują Tagi inteligentne.

## <a name="refactoring"></a>Refaktoryzacja

**Włącz refaktoryzację przy zmianie nazwy**\
Gdy jest ustawiona na `true` , operacja refaktoryzacji zmiany nazwy jest wykonywana po zmianie nazwy składnika z okna okno właściwości lub konspektu dokumentu.

## <a name="toolbox"></a>Przybornik

**Automatycznie Wypełnij Przybornik**\
Określa, czy okno przybornika jest wypełniane automatycznie ze składnikami i kontrolkami skompilowanymi przez projekt.
