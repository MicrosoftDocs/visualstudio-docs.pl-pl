---
title: Dostosuj sposób tworzenia podpisów dla formantów powiązanych z danymi w Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476915"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy przeciągasz elementy z [okna źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na Projektant formularzy systemu Windows, szczególnym zagadnieniem jest odzyskanie: nazwy kolumn w etykietach podpisów są ponownie sformatowane do bardziej czytelnego ciągu, gdy znaleziono dwa lub więcej wyrazów do łączenia ze sobą. Możesz dostosować sposób, w jaki są tworzone te etykiety, ustawiając wartości **SmartCaptionExpression**, **SmartCaptionReplacement**i **SmartCaptionSuffix** w kluczu rejestru **HKEY_CURRENT_USER Projektant \software\microsoft\visualstudio\10.0\Data** .

> [!NOTE]
> Ten klucz rejestru nie istnieje, dopóki nie zostanie utworzony.

 Inteligentne podpisy są kontrolowane przez wyrażenie regularne wprowadzane do wartości **SmartCaptionExpression** wartości. Dodanie klucza rejestru **projektanci danych** zastępuje domyślne wyrażenie regularne, które kontroluje etykiety napisów. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 W poniższej tabeli opisano wartości rejestru, które kontrolują podpis etykiety.

|Element rejestru|Opis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Wyrażenie regularne, które służy do dopasowania Twoich wzorców.|
|**SmartCaptionReplacement**|Format, w którym mają być wyświetlane wszystkie grupy dopasowane do **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Opcjonalny ciąg do dołączenia na końcu podpis.|

 W poniższej tabeli wymieniono ustawienia wewnętrznego ustawienia domyślnego dla tych wartości rejestru.

|Element rejestru|Wartość domyślna|Wyjaśnienie|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124;_+|Dopasowuje znak małej litery następują wielkiej litery lub znaku podkreślenia.|
|**SmartCaptionReplacement**|$1 $2|$1 reprezentuje dowolne znaki dopasowywane w nawiasach pierwszego wyrażenia, a $2 — dowolne znaki dopasowywane w nawiasach drugiego. Zastąpienie jest pierwsze dopasowanie, spację, a następnie drugie dopasowania.|
|**SmartCaptionSuffix**|:|Reprezentuje znak, który został dołączony do zwracanego ciągu. Na przykład, jeśli podpis jest `Company Name`, sufiks spowoduje `Company Name:`|

> [!CAUTION]
> Należy zachować ostrożność w Edytorze rejestru niczym zajęty. Utwórz kopię zapasową rejestru przed jego edycji. Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie gwarantuje, można rozwiązać problemy, które powodują za pomocą Edytora rejestru niepoprawnie. Używasz Edytora rejestru na własne ryzyko.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Aby zmodyfikować zachowanie podpisów inteligentne okna źródeł danych

1. Otwórz okno wiersza polecenia, klikając przycisk **Start** , a następnie polecenie **Uruchom**.

2. W oknie dialogowym **Uruchamianie** wpisz `regedit` i kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER** .

4. Rozwiń węzeł **oprogramowania** .

5. Rozwiń węzeł **Microsoft** .

6. Rozwiń węzeł **VisualStudio** .

7. Kliknij prawym przyciskiem myszy węzeł **10,0** i Utwórz nowy **klucz** o nazwie `Data Designers`.

8. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionExpression`.

9. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionReplacement`.

10. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionSuffix`.

11. Kliknij prawym przyciskiem myszy element **SmartCaptionExpression** i wybierz polecenie **Modyfikuj**.

12. Wprowadź wyrażenie regularne, które ma być używane przez okno **źródeł danych** .

13. Kliknij prawym przyciskiem myszy element **SmartCaptionReplacement** i wybierz polecenie **Modyfikuj**.

14. Zastąpienia wprowadź ciąg sformatowany w sposób mają być wyświetlane wzorców dopasowywane w wyrażeniu regularnym.

15. Kliknij prawym przyciskiem myszy element **SmartCaptionSuffix** i wybierz polecenie **Modyfikuj**.

16. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpis.

     Gdy następnym razem przeciągniesz elementy z okna **źródła danych** , etykiety podpisów zostaną utworzone przy użyciu podanych nowych wartości rejestru.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Aby wyłączyć funkcję inteligentnych podpisów

1. Otwórz okno wiersza polecenia, klikając przycisk **Start** , a następnie polecenie **Uruchom**.

2. W oknie dialogowym **Uruchamianie** wpisz `regedit` i kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER** .

4. Rozwiń węzeł **oprogramowania** .

5. Rozwiń węzeł **Microsoft** .

6. Rozwiń węzeł **VisualStudio** .

7. Kliknij prawym przyciskiem myszy węzeł **10,0** i Utwórz nowy **klucz** o nazwie `Data Designers`.

8. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionExpression`.

9. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionReplacement`.

10. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionSuffix`.

11. Kliknij prawym przyciskiem myszy element **SmartCaptionExpression** i wybierz polecenie **Modyfikuj**.

12. Wprowadź `(.*)` dla wartości. To będzie odpowiadał cały ciąg.

13. Kliknij prawym przyciskiem myszy element **SmartCaptionReplacement** i wybierz polecenie **Modyfikuj**.

14. Wprowadź `$1` dla wartości. Ciąg to zamienia dopasowany wartość, która jest cały ciąg pozostanie niezmieniona.

     Gdy następnym razem przeciągniesz elementy z okna **źródła danych** , etykiety podpisów są tworzone z niezmodyfikowanymi napisami.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
