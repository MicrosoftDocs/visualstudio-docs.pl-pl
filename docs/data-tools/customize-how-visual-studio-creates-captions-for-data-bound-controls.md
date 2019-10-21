---
title: Dostosuj napisy dla formantów powiązanych z danymi
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 932d50d44fbfaa810225ef90c2f5361bc26d9b72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648572"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio

Gdy przeciągasz elementy z [okna źródła danych](add-new-data-sources.md#data-sources-window) do projektanta, szczególna Uwaga: nazwy kolumn w etykietach podpisów są ponownie sformatowane do bardziej czytelnego ciągu, gdy znaleziono dwa lub więcej wyrazów do łączenia ze sobą.

::: moniker range="vs-2017"

Możesz dostosować sposób, w jaki te etykiety są tworzone przez ustawienie wartości **SmartCaptionExpression**, **SmartCaptionReplacement**i **SmartCaptionSuffix** w **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0 Klucz rejestru projektantów \data** .

::: moniker-end

::: moniker range=">=vs-2019"

Możesz dostosować sposób, w jaki te etykiety są tworzone przez ustawienie wartości **SmartCaptionExpression**, **SmartCaptionReplacement**i **SmartCaptionSuffix** w **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0 Klucz rejestru projektantów \data** .

::: moniker-end

> [!NOTE]
> Ten klucz rejestru nie istnieje, dopóki nie zostanie utworzony.

Inteligentne podpisy są kontrolowane przez wyrażenie regularne wprowadzane do wartości **SmartCaptionExpression** wartości. Dodanie klucza rejestru **projektanci danych** zastępuje domyślne wyrażenie regularne, które kontroluje etykiety napisów. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

W poniższej tabeli opisano wartości rejestru sterujące etykietami napisów.

|Element rejestru|Opis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Wyrażenie regularne używane do dopasowania wzorców.|
|**SmartCaptionReplacement**|Format, w którym mają być wyświetlane wszystkie grupy dopasowane do **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Opcjonalny ciąg do dołączenia na końcu podpisu.|

W poniższej tabeli wymieniono wewnętrzne ustawienia domyślne dla tych wartości rejestru.

|Element rejestru|Wartość domyślna|Wyjaśnienie|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Dopasowuje małą literę, a po niej znak pisany wielką literą lub podkreślenie.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** reprezentuje wszystkie znaki dopasowane w pierwszym nawiasie wyrażenia, a **$2** reprezentuje wszystkie znaki dopasowane w drugim nawiasie. Zastępowanie to pierwsze dopasowanie, spacja, a następnie drugie dopasowanie.|
|**SmartCaptionSuffix**|**:**|Reprezentuje znak dołączony do zwracanego ciągu. Na przykład, jeśli podpis jest `Company Name`, sufiks spowoduje `Company Name:`|

> [!CAUTION]
> Należy zachować ostrożność podczas wykonywania jakichkolwiek czynności w Edytorze rejestru. Przed rozpoczęciem edycji wykonaj kopię zapasową rejestru. Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Firma Microsoft nie gwarantuje, że problemy, których przyczyną jest nieprawidłowe użycie Edytora rejestru, mogą zostać rozpoznane. Używasz Edytora rejestru na własne ryzyko.
>
> Aby uzyskać informacje na temat tworzenia kopii zapasowej, edytowania i przywracania rejestru, zobacz [informacje dotyczące rejestru systemu Windows dla zaawansowanych użytkowników](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Zmodyfikuj inteligentne zachowanie napisów w oknie źródła danych

1. Otwórz okno wiersza polecenia, klikając przycisk **Start** , a następnie polecenie **Uruchom**.

2. W oknie dialogowym **Uruchamianie** wpisz `regedit` i kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER**  > **Software**  > **Microsoft**  > **VisualStudio** .

::: moniker range="vs-2017"

4. Kliknij prawym przyciskiem myszy węzeł **15,0** i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Kliknij prawym przyciskiem myszy węzeł **16,0** i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

5. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz trzy nowe wartości ciągu:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Kliknij prawym przyciskiem myszy wartość **SmartCaptionExpression** , a następnie wybierz polecenie **Modyfikuj**.

7. Wprowadź wyrażenie regularne, które ma być używane przez okno **źródeł danych** .

8. Kliknij prawym przyciskiem myszy wartość **SmartCaptionReplacement** , a następnie wybierz polecenie **Modyfikuj**.

9. Wprowadź ciąg zamiany sformatowany w sposób, w jaki chcesz wyświetlić wzorce dopasowane do wyrażenia regularnego.

10. Kliknij prawym przyciskiem myszy wartość **SmartCaptionSuffix** , a następnie wybierz polecenie **Modyfikuj**.

11. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpisu.

    Gdy następnym razem przeciągniesz elementy z okna **źródła danych** , etykiety podpisów zostaną utworzone przy użyciu podanych nowych wartości rejestru.

## <a name="turn-off-the-smart-captioning-feature"></a>Wyłącz funkcję podpisów inteligentnych

1. Otwórz okno wiersza polecenia, klikając przycisk **Start** , a następnie polecenie **Uruchom**.

2. W oknie dialogowym **Uruchamianie** wpisz `regedit` i kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER**  > **Software**  > **Microsoft**  > **VisualStudio** .

::: moniker range="vs-2017"

4. Kliknij prawym przyciskiem myszy węzeł **15,0** i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Kliknij prawym przyciskiem myszy węzeł **16,0** i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

5. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz trzy nowe wartości ciągu:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Kliknij prawym przyciskiem myszy element **SmartCaptionExpression** i wybierz polecenie **Modyfikuj**.

7. Wprowadź `(.*)` dla wartości. Będzie to zgodne z całym ciągiem.

8. Kliknij prawym przyciskiem myszy element **SmartCaptionReplacement** i wybierz polecenie **Modyfikuj**.

9. Wprowadź `$1` dla wartości. Spowoduje to zamienienie ciągu z dopasowaną wartością, czyli cały ciąg, tak aby pozostały niezmieniony.

    Gdy następnym razem przeciągniesz elementy z okna **źródła danych** , etykiety podpisów są tworzone z niezmodyfikowanymi napisami.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)