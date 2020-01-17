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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f7780cfb3b266de6f477e74d1b352cf6b24aab42
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113662"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio

Gdy przeciągasz elementy z [okna źródła danych](add-new-data-sources.md#data-sources-window) do projektanta, szczególna Uwaga: nazwy kolumn w etykietach podpisów są ponownie sformatowane do bardziej czytelnego ciągu, gdy znaleziono dwa lub więcej wyrazów do łączenia ze sobą.

::: moniker range="vs-2017"

Możesz dostosować sposób, w jaki te etykiety są tworzone przez ustawienie wartości **SmartCaptionExpression**, **SmartCaptionReplacement**i **SmartCaptionSuffix** w kluczu rejestru **HKEY_CURRENT_USER Projektant \software\microsoft\visualstudio\15.0\Data** .

::: moniker-end

::: moniker range=">=vs-2019"

Możesz dostosować sposób, w jaki te etykiety są tworzone przez ustawienie wartości **SmartCaptionExpression**, **SmartCaptionReplacement**i **SmartCaptionSuffix** w kluczu rejestru **HKEY_CURRENT_USER Projektant \software\microsoft\visualstudio\16.0\Data** .

::: moniker-end

> [!NOTE]
> Ten klucz rejestru nie istnieje, dopóki nie zostanie utworzony.

Podpisy inteligentne jest kontrolowany przez wyrażenia regularne zawierana wartość **SmartCaptionExpression** wartości. Dodawanie **projektantów danych** klucza rejestru zastępuje domyślne wyrażenie regularne, które kontrolki etykiety podpis. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

W poniższej tabeli opisano wartości rejestru, które kontrolują podpis etykiety.

|Element rejestru|Opis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Wyrażenie regularne używane do dopasowania wzorców.|
|**SmartCaptionReplacement**|Format wyświetlania żadnych grup dopasowywany **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Opcjonalny ciąg do dołączenia na końcu podpis.|

W poniższej tabeli wymieniono ustawienia wewnętrznego ustawienia domyślnego dla tych wartości rejestru.

|Element rejestru|Wartość domyślna|Wyjaśnienie|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Dopasowuje znak małej litery następują wielkiej litery lub znaku podkreślenia.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** reprezentuje wszystkie znaki dopasowane w pierwszym nawiasie wyrażenia, a **$2** reprezentuje wszystkie znaki dopasowane w drugim nawiasie. Zastąpienie jest pierwsze dopasowanie, spację, a następnie drugie dopasowania.|
|**SmartCaptionSuffix**|**:**|Reprezentuje znak, który został dołączony do zwracanego ciągu. Na przykład, jeśli podpis jest `Company Name`, sufiks sprawia, że `Company Name:`|

> [!CAUTION]
> Należy zachować ostrożność podczas wykonywania jakichkolwiek czynności w Edytorze rejestru. Utwórz kopię zapasową rejestru przed jego edycji. Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie gwarantuje, można rozwiązać problemy, które powodują za pomocą Edytora rejestru niepoprawnie. Używasz Edytora rejestru na własne ryzyko.
>
> Aby uzyskać informacje na temat tworzenia kopii zapasowej, edytowania i przywracania rejestru, zobacz [informacje dotyczące rejestru systemu Windows dla zaawansowanych użytkowników](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Zmodyfikuj inteligentne zachowanie napisów w oknie źródła danych

1. Otwórz okno polecenia, klikając **Start** i następnie **Uruchom**.

2. Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER** > **oprogramowania** > **Microsoft** > **VisualStudio** .

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

7. Wprowadź wyrażenie regularne ma **źródeł danych** okna do użycia.

8. Kliknij prawym przyciskiem myszy wartość **SmartCaptionReplacement** , a następnie wybierz polecenie **Modyfikuj**.

9. Zastąpienia wprowadź ciąg sformatowany w sposób mają być wyświetlane wzorców dopasowywane w wyrażeniu regularnym.

10. Kliknij prawym przyciskiem myszy wartość **SmartCaptionSuffix** , a następnie wybierz polecenie **Modyfikuj**.

11. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpis.

    Przy następnym przeciągnij elementy z **źródeł danych** oknie etykiety podpis są tworzone przy użyciu nowej wartości rejestru, pod warunkiem.

## <a name="turn-off-the-smart-captioning-feature"></a>Wyłącz funkcję podpisów inteligentnych

1. Otwórz okno polecenia, klikając **Start** i następnie **Uruchom**.

2. Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER** > **oprogramowania** > **Microsoft** > **VisualStudio** .

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

6. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** elementu, a następnie wybierz **Modyfikuj**.

7. Wprowadź `(.*)` dla wartości. To będzie odpowiadał cały ciąg.

8. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** elementu, a następnie wybierz **Modyfikuj**.

9. Wprowadź `$1` dla wartości. Ciąg to zamienia dopasowany wartość, która jest cały ciąg pozostanie niezmieniona.

    Przy następnym przeciągnij elementy z **źródeł danych** oknie etykiety podpis są tworzone przy użyciu transkrypcji zostały zmodyfikowane.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
