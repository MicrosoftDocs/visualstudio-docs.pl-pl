---
title: Dostosowywanie podpisów dla formantów powiązanych z danymi
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1745aef29da9fc8efd49789f0112c903128f6f74
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323707"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio

Podczas przeciągania elementów z [okna źródeł danych](add-new-data-sources.md#data-sources-window) do projektanta szczególną uwagę właśnie: nazwy kolumn w etykietach podpis jest umieszczany w ciąg bardziej czytelny, gdy dwie lub więcej słów okaże się, że połączone ze sobą.

::: moniker range="vs-2017"

Można dostosować sposób, w którym te etykiety są tworzone przez ustawienie **SmartCaptionExpression**, **SmartCaptionReplacement**, i **SmartCaptionSuffix** wartości w **projektantów HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data** klucza rejestru.

::: moniker-end

::: moniker range=">=vs-2019"

Można dostosować sposób, w którym te etykiety są tworzone przez ustawienie **SmartCaptionExpression**, **SmartCaptionReplacement**, i **SmartCaptionSuffix** wartości w **projektantów HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data** klucza rejestru.

::: moniker-end

> [!NOTE]
> Ten klucz rejestru nie istnieje, dopóki nie zostanie utworzony.

Podpisy inteligentne jest kontrolowany przez wyrażenia regularne zawierana wartość **SmartCaptionExpression** wartości. Dodawanie **projektantów danych** klucza rejestru zastępuje domyślne wyrażenie regularne, które kontrolki etykiety podpis. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

W poniższej tabeli opisano wartości rejestru, które kontrolują podpis etykiety.

|Element rejestru|Opis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Wyrażenie regularne używane do dopasowania Twoich wzorców.|
|**SmartCaptionReplacement**|Format wyświetlania żadnych grup dopasowywany **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Opcjonalny ciąg do dołączenia na końcu podpis.|

W poniższej tabeli wymieniono ustawienia wewnętrznego ustawienia domyślnego dla tych wartości rejestru.

|Element rejestru|Wartość domyślna|Wyjaśnienie|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Dopasowuje znak małej litery następują wielkiej litery lub znaku podkreślenia.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** reprezentuje dowolne znaki dopasowywane w nawiasach pierwszego wyrażenia, a **$2** reprezentuje dowolne znaki dopasowywane w nawiasach drugiego. Zastąpienie jest pierwsze dopasowanie, spację, a następnie drugie dopasowania.|
|**SmartCaptionSuffix**|**:**|Reprezentuje znak, który został dołączony do zwracanego ciągu. Na przykład, jeśli podpis jest `Company Name`, sufiks sprawia, że `Company Name:`|

> [!CAUTION]
> Należy zachować ostrożność w Edytorze rejestru niczym zajęty. Utwórz kopię zapasową rejestru przed jego edycji. Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie gwarantuje, można rozwiązać problemy, które powodują za pomocą Edytora rejestru niepoprawnie. Używasz Edytora rejestru na własne ryzyko.
>
> Aby uzyskać informacje o tworzeniu kopii zapasowych, edytowanie i przywracania rejestru, zobacz [Windows informacji rejestru dla użytkowników zaawansowanych](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modyfikowanie zachowania podpisów inteligentne okna źródeł danych

1. Otwórz okno polecenia, klikając **Start** i następnie **Uruchom**.

2. Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3. Rozwiń **HKEY_CURRENT_USER** > **oprogramowania** > **Microsoft** > **VisualStudio**węzła.

::: moniker range="vs-2017"

4. Kliknij prawym przyciskiem myszy **15.0** węzeł i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Kliknij prawym przyciskiem myszy **16.0** węzeł i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

5. Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz trzy nowe wartości ciągu:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** wartości, a następnie wybierz **Modyfikuj**.

7. Wprowadź wyrażenie regularne ma **źródeł danych** okna do użycia.

8. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** wartości, a następnie wybierz **Modyfikuj**.

9. Zastąpienia wprowadź ciąg sformatowany w sposób mają być wyświetlane wzorców dopasowywane w wyrażeniu regularnym.

10. Kliknij prawym przyciskiem myszy **SmartCaptionSuffix** wartości, a następnie wybierz **Modyfikuj**.

11. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpis.

    Przy następnym przeciągnij elementy z **źródeł danych** oknie etykiety podpis są tworzone przy użyciu nowej wartości rejestru, pod warunkiem.

## <a name="turn-off-the-smart-captioning-feature"></a>Wyłącz funkcję inteligentnych funkcji podpisów

1. Otwórz okno polecenia, klikając **Start** i następnie **Uruchom**.

2. Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3. Rozwiń **HKEY_CURRENT_USER** > **oprogramowania** > **Microsoft** > **VisualStudio**węzła.

::: moniker range="vs-2017"

4. Kliknij prawym przyciskiem myszy **15.0** węzeł i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Kliknij prawym przyciskiem myszy **16.0** węzeł i Utwórz nowy **klucz** o nazwie `Data Designers`.

::: moniker-end

5. Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz trzy nowe wartości ciągu:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** elementu, a następnie wybierz **Modyfikuj**.

7. Wprowadź `(.*)` dla wartości. To będzie odpowiadał cały ciąg.

8. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** elementu, a następnie wybierz **Modyfikuj**.

9. Wprowadź `$1` dla wartości. Ciąg to zamienia dopasowany wartość, która jest cały ciąg pozostanie niezmieniona.

    Przy następnym przeciągnij elementy z **źródeł danych** oknie etykiety podpis są tworzone przy użyciu transkrypcji zostały zmodyfikowane.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)