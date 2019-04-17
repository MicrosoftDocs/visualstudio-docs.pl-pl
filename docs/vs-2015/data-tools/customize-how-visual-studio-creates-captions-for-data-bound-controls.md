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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 20611035ba37c509be7e41d8468d0c3d893334b2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647962"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas przeciągania elementów z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na Windows Forms Designer szczególną uwagę właśnie: nazwy kolumn w etykietach podpis jest umieszczany w ciąg bardziej czytelny, gdy dwie lub więcej słów są Znaleziono ze sobą połączonych. Można dostosować sposób tworzenia tych etykiet, ustawiając **SmartCaptionExpression**, **SmartCaptionReplacement**, i **SmartCaptionSuffix** wartości w **projektantów HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data** klucza rejestru.

> [!NOTE]
>  Ten klucz rejestru nie istnieje, dopóki nie zostanie utworzony.

 Podpisy inteligentne jest kontrolowany przez wyrażenia regularne zawierana wartość **SmartCaptionExpression** wartości. Dodawanie **projektantów danych** klucza rejestru zastępuje domyślne wyrażenie regularne, które kontrolki etykiety podpis. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 W poniższej tabeli opisano wartości rejestru, które kontrolują podpis etykiety.

|Element rejestru|Opis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Wyrażenie regularne, które służy do dopasowania Twoich wzorców.|
|**SmartCaptionReplacement**|Format wyświetlania żadnych grup dopasowywany **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Opcjonalny ciąg do dołączenia na końcu podpis.|

 W poniższej tabeli wymieniono ustawienia wewnętrznego ustawienia domyślnego dla tych wartości rejestru.

|Element rejestru|Wartość domyślna|Wyjaśnienie|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Dopasowuje znak małej litery następują wielkiej litery lub znaku podkreślenia.|
|**SmartCaptionReplacement**|$1 $2|$1 reprezentuje dowolne znaki dopasowywane w nawiasach pierwszego wyrażenia, a $2 — dowolne znaki dopasowywane w nawiasach drugiego. Zastąpienie jest pierwsze dopasowanie, spację, a następnie drugie dopasowania.|
|**SmartCaptionSuffix**|:|Reprezentuje znak, który został dołączony do zwracanego ciągu. Na przykład, jeśli podpis jest `Company Name`, sufiks sprawia, że `Company Name:`|

> [!CAUTION]
>  Należy zachować ostrożność w Edytorze rejestru niczym zajęty. Utwórz kopię zapasową rejestru przed jego edycji. Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie gwarantuje, można rozwiązać problemy, które powodują za pomocą Edytora rejestru niepoprawnie. Używasz Edytora rejestru na własne ryzyko.
>
>  W poniższym artykule bazy wiedzy zawiera instrukcje dotyczące tworzenia kopii zapasowej, edytowanie i przywracania rejestru: [Opis rejestru firmy Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Aby zmodyfikować zachowanie podpisów inteligentne okna źródeł danych

1.  Otwórz okno polecenia, klikając **Start** i następnie **Uruchom**.

2.  Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3.  Rozwiń **HKEY_CURRENT_USER** węzła.

4.  Rozwiń **oprogramowania** węzła.

5.  Rozwiń **Microsoft** węzła.

6.  Rozwiń **VisualStudio** węzła.

7.  Kliknij prawym przyciskiem myszy **10.0** węzeł i Utwórz nowy **klucz** o nazwie `Data Designers`.

8.  Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz nowy **wartość ciągu** o nazwie `SmartCaptionExpression`.

9. Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz nowy **wartość ciągu** o nazwie `SmartCaptionReplacement`.

10. Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz nowy **wartość ciągu** o nazwie `SmartCaptionSuffix`.

11. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** elementu, a następnie wybierz **Modyfikuj**.

12. Wprowadź wyrażenie regularne ma **źródeł danych** okna do użycia.

13. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** elementu, a następnie wybierz **Modyfikuj**.

14. Zastąpienia wprowadź ciąg sformatowany w sposób mają być wyświetlane wzorców dopasowywane w wyrażeniu regularnym.

15. Kliknij prawym przyciskiem myszy **SmartCaptionSuffix** elementu, a następnie wybierz **Modyfikuj**.

16. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpis.

     Przy następnym przeciągnij elementy z **źródeł danych** oknie etykiety podpis są tworzone przy użyciu nowej wartości rejestru, pod warunkiem.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Aby wyłączyć funkcję inteligentnych podpisów

1.  Otwórz okno polecenia, klikając **Start** i następnie **Uruchom**.

2.  Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3.  Rozwiń **HKEY_CURRENT_USER** węzła.

4.  Rozwiń **oprogramowania** węzła.

5.  Rozwiń **Microsoft** węzła.

6.  Rozwiń **VisualStudio** węzła.

7.  Kliknij prawym przyciskiem myszy **10.0** węzeł i Utwórz nowy **klucz** o nazwie `Data Designers`.

8.  Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz nowy **wartość ciągu** o nazwie `SmartCaptionExpression`.

9. Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz nowy **wartość ciągu** o nazwie `SmartCaptionReplacement`.

10. Kliknij prawym przyciskiem myszy **projektantów danych** węzeł i Utwórz nowy **wartość ciągu** o nazwie `SmartCaptionSuffix`.

11. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** elementu, a następnie wybierz **Modyfikuj**.

12. Wprowadź `(.*)` dla wartości. To będzie odpowiadał cały ciąg.

13. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** elementu, a następnie wybierz **Modyfikuj**.

14. Wprowadź `$1` dla wartości. Ciąg to zamienia dopasowany wartość, która jest cały ciąg pozostanie niezmieniona.

     Przy następnym przeciągnij elementy z **źródeł danych** oknie etykiety podpis są tworzone przy użyciu transkrypcji zostały zmodyfikowane.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
