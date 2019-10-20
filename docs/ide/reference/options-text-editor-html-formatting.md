---
title: Opcje, Edytor tekstu, HTML (Formularze sieci Web), formatowanie
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d1e5f07a2b68d86051452a16ac0f42fc9b9acf0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666193"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opcje, Edytor tekstu, HTML (Formularze sieci Web), formatowanie

Strona Opcje **formatowania** służy do ustawiania opcji projektu HTML służących do formatowania kodu w edytorze kodu. Aby uzyskać dostęp do tej strony, na pasku menu wybierz pozycję **narzędzia**  > **Opcje**, a następnie rozwiń węzeł **Edytor tekstu**  > **HTML (Formularze sieci Web)**  > **Formatowanie**.

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
|**Znaki**|Nazwy elementów są formatowane wielką literą.|
|**Dużych**|Nazwy elementów są formatowane małymi literami.|
|**Definicja zestawu**|Przypadek elementu jest określany przez sposób, w jaki element jest zdefiniowany w odpowiedniej klasie typu.|

**Tag klienta, atrybuty klienta**

Te opcje określają, czy automatyczne formatowanie zmienia nazwy atrybutów i właściwości HTML na wielkie lub małe litery, czy też zachowuje je zgodnie z wprowadzonymi danymi.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Zgodnie z wprowadzonymi**|Wielkość liter atrybutu jest dokładnie wprowadzona.|
|**Znaki**|Nazwy atrybutów są formatowane wielką literą.|
|**Dużych**|Nazwy atrybutów są formatowane małymi literami.|

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

   Gdy ta opcja jest zaznaczona, Edytor automatycznie tworzy tag zamykający (na przykład **\</b >** ) po zamknięciu tagu otwierającego.

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

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)