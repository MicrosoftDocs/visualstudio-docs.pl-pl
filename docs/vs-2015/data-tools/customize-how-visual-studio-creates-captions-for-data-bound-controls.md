---
title: Dostosuj sposób, w jaki program Visual Studio 2015 tworzy napisy dla formantów powiązanych z danymi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476915"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy przeciągasz elementy z [okna źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na Projektant formularzy systemu Windows, szczególnym zagadnieniem jest odzyskanie: nazwy kolumn w etykietach podpisów są ponownie sformatowane do bardziej czytelnego ciągu, gdy znaleziono dwa lub więcej wyrazów do łączenia ze sobą. Możesz dostosować sposób, w jaki są tworzone te etykiety, ustawiając wartości **SmartCaptionExpression**, **SmartCaptionReplacement**i **SmartCaptionSuffix** w kluczu rejestru **HKEY_CURRENT_USER Projektant \software\microsoft\visualstudio\10.0\Data** .

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
|**SmartCaptionExpression**|( \\ \p{LL}) ( \\ \p{Lu}) &#124;_ +|Dopasowuje małą literę, a po niej znak pisany wielką literą lub podkreślenie.|
|**SmartCaptionReplacement**|$1 $2|$1 reprezentuje wszystkie znaki dopasowane w pierwszym nawiasie wyrażenia, a $2 reprezentuje wszystkie znaki dopasowane w drugim nawiasie. Zastępowanie to pierwsze dopasowanie, spacja, a następnie drugie dopasowanie.|
|**SmartCaptionSuffix**|:|Reprezentuje znak dołączony do zwracanego ciągu. Na przykład, jeśli podpis ma wartość `Company Name` , sufiks czyni go `Company Name:`|

> [!CAUTION]
> Należy zachować ostrożność podczas wykonywania jakichkolwiek czynności w Edytorze rejestru. Przed rozpoczęciem edycji wykonaj kopię zapasową rejestru. Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Firma Microsoft nie gwarantuje, że problemy, których przyczyną jest nieprawidłowe użycie Edytora rejestru, mogą zostać rozpoznane. Używasz Edytora rejestru na własne ryzyko.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Aby zmodyfikować zachowanie inteligentnego podpisu okna źródeł danych

1. Otwórz okno wiersza polecenia, klikając przycisk **Start** , a następnie polecenie **Uruchom**.

2. Wpisz `regedit` w oknie dialogowym **Uruchamianie** , a następnie kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER** .

4. Rozwiń węzeł **oprogramowania** .

5. Rozwiń węzeł **Microsoft** .

6. Rozwiń węzeł **VisualStudio** .

7. Kliknij prawym przyciskiem myszy węzeł **10,0** i Utwórz nowy **klucz** o nazwie `Data Designers` .

8. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionExpression` .

9. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionReplacement` .

10. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionSuffix` .

11. Kliknij prawym przyciskiem myszy element **SmartCaptionExpression** i wybierz polecenie **Modyfikuj**.

12. Wprowadź wyrażenie regularne, które ma być używane przez okno **źródeł danych** .

13. Kliknij prawym przyciskiem myszy element **SmartCaptionReplacement** i wybierz polecenie **Modyfikuj**.

14. Wprowadź ciąg zamiany sformatowany w sposób, w jaki chcesz wyświetlić wzorce dopasowane do wyrażenia regularnego.

15. Kliknij prawym przyciskiem myszy element **SmartCaptionSuffix** i wybierz polecenie **Modyfikuj**.

16. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpisu.

     Gdy następnym razem przeciągniesz elementy z okna **źródła danych** , etykiety podpisów zostaną utworzone przy użyciu podanych nowych wartości rejestru.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Aby wyłączyć funkcję podpisów inteligentnych

1. Otwórz okno wiersza polecenia, klikając przycisk **Start** , a następnie polecenie **Uruchom**.

2. Wpisz `regedit` w oknie dialogowym **Uruchamianie** , a następnie kliknij przycisk **OK**.

3. Rozwiń węzeł **HKEY_CURRENT_USER** .

4. Rozwiń węzeł **oprogramowania** .

5. Rozwiń węzeł **Microsoft** .

6. Rozwiń węzeł **VisualStudio** .

7. Kliknij prawym przyciskiem myszy węzeł **10,0** i Utwórz nowy **klucz** o nazwie `Data Designers` .

8. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionExpression` .

9. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionReplacement` .

10. Kliknij prawym przyciskiem myszy węzeł **projektanci danych** i Utwórz nową **wartość ciągu** o nazwie `SmartCaptionSuffix` .

11. Kliknij prawym przyciskiem myszy element **SmartCaptionExpression** i wybierz polecenie **Modyfikuj**.

12. Wprowadź `(.*)` wartość. Będzie to zgodne z całym ciągiem.

13. Kliknij prawym przyciskiem myszy element **SmartCaptionReplacement** i wybierz polecenie **Modyfikuj**.

14. Wprowadź `$1` wartość. Spowoduje to zamienienie ciągu z dopasowaną wartością, czyli cały ciąg, tak aby pozostały niezmieniony.

     Gdy następnym razem przeciągniesz elementy z okna **źródła danych** , etykiety podpisów są tworzone z niezmodyfikowanymi napisami.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
