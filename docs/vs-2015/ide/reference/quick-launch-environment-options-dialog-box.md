---
title: Szybkie uruchamianie, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: abd8f8e9ee35c234a79af74199b11d5491e6fbee
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851632"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Szybkie uruchamianie, środowisko, opcje — okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Funkcja **szybkiego uruchamiania** umożliwia szybkie wyszukiwanie i wykonywanie akcji dla zasobów IDE, takich jak opcje, szablony i menu. Nie można użyć **szybkiego uruchamiania** do wyszukiwania kodu i symboli. Pole wyszukiwania **szybkiego uruchamiania** znajduje się w prawym górnym rogu paska menu i jest dostępne po wybraniu klawiszy CTRL + Q. Wystarczy wprowadzić ciąg wyszukiwania w polu. Do wyszukiwania ciągów zawierających @, użyj ”@@”.

 **Szybkie uruchamianie** jest domyślnie włączone podczas instalowania programu Visual Studio. Na pasku menu można pokazać lub ukryć pasek **Szybkie uruchamianie** , wybierając pozycję **Narzędzia**, **Opcje**. Rozwiń węzeł **środowiska** , a następnie wybierz polecenie **Szybkie uruchamianie**. Zaznacz lub wyczyść pole wyboru **Włącz szybkie uruchamianie** . Możesz również włączyć lub wyłączyć kategorie wyszukiwania na tej stronie.

## <a name="category-list"></a>Lista kategorii
 Wyniki wyszukiwania szybkiego uruchamiania są wyświetlane w czterech kategoriach: **ostatnio używane**, **menu**, **Opcje**i **otwarte dokumenty**wraz z liczbą elementów w kategorii. Aby przechodzić przez wyniki wyszukiwania według kategorii, wybierz klawisze CTRL + Q, aby wyświetlić wszystkie wyniki z kolejnej kategorii. Po wyświetleniu ostatniej kategorii Ctrl + Q pokazuje kilka wyników z każdej kategorii. Możesz użyć klawiszy Ctrl + Shift + Q, aby nawigować przez kategorie w odwrotnej kolejności. Aby wyświetlić wszystkie wyniki wyszukiwania w kategorii, wybierz nazwę kategorii.

 Możesz użyć następujących skrótów, aby ograniczyć wyszukiwanie do określonych kategorii.

|Kategoria|Skrót|Opis skrótu|
|--------------|--------------|--------------------------|
|Ostatnio używane|@mru<br /><br /> Na przykład:`@mru font`|Wyświetla maksymalnie pięć elementów, które były **ostatnio używane**.|
|Menu|@menu<br /><br /> Na przykład:`@menu font`|Ogranicza wyszukiwanie do elementów menu.|
|Opcje|@opt<br /><br /> Na przykład:`@opt font`|Ogranicza wyszukiwanie do ustawień w oknie dialogowym **Opcje** .|
|Dokumenty|@doc<br /><br /> Na przykład:`@doc font`|Ogranicza wyszukiwanie do nazw plików i ścieżek otwartych dokumentów dla kryteriów wyszukiwania, ale nie przeszukuje tekstu wewnątrz samych plików.|

> [!NOTE]
> Można zmienić klawisze skrótów na stronie **Ogólne**, **Klawiatura** w oknie dialogowym **Opcje** .

## <a name="show-previous-results"></a>Pokaż poprzednie wyniki
 Wprowadzony termin wyszukiwania nie jest domyślnie utrwalany między sesjami wyszukiwania. Ciąg wyszukiwania jest wyczyszczony, jeśli szukasz terminu, Przenieś kursor poza obszar **szybkiego uruchamiania** , a następnie wróć. Aby zachować wyniki wyszukiwania, przejdź do okna dialogowego **Opcje** , wybierz pozycję **Szybkie uruchamianie**, a następnie wybierz pozycję **Pokaż wyniki wyszukiwania z poprzedniego wyszukiwania, gdy szybkie uruchamianie jest aktywowane.** . Przy następnym przeszukiwaniu pozostaw obszar szybkie uruchamianie i Wróć, szybkie uruchamianie spowoduje zachowanie ostatniego użytego terminu wyszukiwania, a także wyświetlenie wyników wyszukiwania.

 Najnowsze porady i wskazówki dotyczące korzystania z funkcji **szybkiego uruchamiania**można znaleźć [na blogu programu Visual Studio](https://blogs.msdn.com/b/visualstudio/).

## <a name="see-also"></a>Zobacz też
 [Ogólne elementy interfejsu użytkownika (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md) — okno [dialogowe Opcje środowiska](../../ide/reference/environment-options-dialog-box.md)
