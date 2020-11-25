---
title: Opcje, Edytor tekstu, HTML (Formularze sieci Web), formatowanie
description: Informacje na temat używania strony formatowania w sekcji HTML do ustawiania opcji projektu HTML służących do formatowania kodu w edytorze kodu.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c8fe85b7bce856867802d43411816ae2df5d2c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040982"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opcje, Edytor tekstu, HTML (Formularze sieci Web), formatowanie

Strona Opcje **formatowania** służy do ustawiania opcji projektu HTML służących do formatowania kodu w edytorze kodu. Aby uzyskać dostęp do tej strony, na pasku menu wybierz **Tools**  >  **Opcje** narzędzia, a następnie rozwiń pozycję formatowanie **Edytor tekstu**  >  **HTML (Formularze sieci Web)**  >  **Formatting**.

## <a name="capitalization"></a>Wielkość liter

Po wybraniu tych opcji Widok źródłowy i Edytor XML zastosują domyślny format wielkości liter do nazw elementów i atrybutów podczas pierwszego tworzenia elementów i podczas automatycznego formatowania. Ustawienia **Zastosuj automatyczne formatowanie** określają czas, w którym następuje automatyczne ponowne formatowanie.

> [!WARNING]
> W pliku XML jest rozróżniana wielkość liter. Ustawienie domyślnego przypadku może mieć wpływ na parsery XML.

### <a name="uielement-list"></a>Lista elementów UIElement

**Tag serwera, atrybuty serwera**

Te opcje określają sposób, w jaki znaczniki formantów serwera sieci Web są pisane wielkimi literami.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Zgodnie z wprowadzonymi**|Wielkość liter elementu jest dokładnie wprowadzona.|
|**Wielkie litery**|Nazwy elementów są formatowane wielką literą.|
|**Małe litery**|Nazwy elementów są formatowane małymi literami.|
|**Definicja zestawu**|Przypadek elementu jest określany przez sposób, w jaki element jest zdefiniowany w odpowiedniej klasie typu.|

**Tag klienta, atrybuty klienta**

Te opcje określają, czy automatyczne formatowanie zmienia nazwy atrybutów i właściwości HTML na wielkie lub małe litery, czy też zachowuje je zgodnie z wprowadzonymi danymi.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Zgodnie z wprowadzonymi**|Wielkość liter atrybutu jest dokładnie wprowadzona.|
|**Wielkie litery**|Nazwy atrybutów są formatowane wielką literą.|
|**Małe litery**|Nazwy atrybutów są formatowane małymi literami.|

## <a name="automatic-formatting-options"></a>Opcje formatowania automatycznego

Te opcje powodują, że Edytor widoku źródła dodaje lub usuwa przerwy w linii fizycznej podczas automatycznego formatowania. Można również określić, czy edytor ma dodawać cudzysłowy wokół atrybutów.

> [!NOTE]
> Te ustawienia nie zmieniają odstępów w znacznikach XML.

### <a name="uielement-list"></a>Lista elementów UIElement

- **Wstaw cudzysłowy wartości atrybutów podczas wpisywania**

   Po wybraniu tej opcji edytor automatycznie umieszcza znaki cudzysłowu wokół atrybutów podczas pisania (na przykład: ID = "Select1"). Usuń zaznaczenie tej opcji, jeśli wolisz ręcznie wstawiać znaczniki cudzysłowu do znaczników.

   > [!NOTE]
   > Niezależnie od tego, czy ta opcja jest zaznaczona, wszystkie istniejące znaki cudzysłowu w znaczniku są zachowywane; znaki cudzysłowu nigdy nie są usuwane.

- **Wstaw cudzysłowy wartości atrybutów podczas formatowania**

   Gdy ta opcja jest zaznaczona, automatyczne formatowanie dodaje znaki cudzysłowu otaczające wartości atrybutów (na przykład: ID = "Select1").

   > [!NOTE]
   > Niezależnie od tego, czy ta opcja jest zaznaczona, wszystkie istniejące znaki cudzysłowu w znaczniku są zachowywane.

- **Autouzupełnianie Wstaw tag zamykający**

   Gdy ta opcja jest zaznaczona, Edytor automatycznie tworzy tag zamykający (na przykład **\</b>** ) po zamknięciu tagu otwierającego.

## <a name="tag-wrapping"></a>Zawijanie tagów

Te opcje określają, czy Edytor dzieli znaczniki do wierszy, jeśli wykraczają poza określoną długość.

### <a name="uielement-list"></a>Lista elementów UIElement

- **Zawijaj tagi, gdy przekracza określoną długość**

   Po wybraniu Edytor dzieli znaczniki między wierszami, Jeśli znacznik wykracza poza długość określoną w polu tekstowym **Długość** . Ta akcja występuje tylko w przypadku formatowania znacznika, a nie w przypadku wpisywania nowego tagu.

   > [!NOTE]
   > Określona wartość jest używana jako wartość minimalna. Edytor nie przerywa pojedynczych atrybutów.

- **Długość**

   Określa liczbę znaków wyświetlanych w wierszu przed otoką. To pole wejściowe jest wyłączone, chyba że jest zaznaczone pole wyboru **Otocz znaczniki po przekroczeniu pola o określonej długości** .

- **Opcje dotyczące tagów**

   Wyświetla okno dialogowe **Opcje charakterystyczne dla tagów** , które umożliwia ustawianie opcji formatowania dla poszczególnych tagów lub grup znaczników.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
