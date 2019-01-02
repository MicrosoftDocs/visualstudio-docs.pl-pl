---
title: Dostosowywanie i rozszerzanie języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 165798341f08afd3b55e8f6b8092457f022a0634
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960040"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Dostosowywanie i rozszerzanie języka specyficznego dla domeny
Program Visual Studio do modelowania i zestaw SDK wizualizacji (VMSDK) zawiera kilka poziomów, w których można zdefiniować narzędzi do modelowania:

1.  Definiowanie języka właściwego dla domeny (DSL), za pomocą diagramem definicji DSL. Możesz szybko utworzyć DSL za pomocą notacji diagramowy, czytelny formularza XML i podstawowe narzędzia, które są wymagane do generowania kodu i innych artefaktów.

     Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

2.  Dostosuj język DSL za pomocą bardziej zaawansowanych funkcji w definicji DSL. Na przykład można wprowadzić dodatkowe linki, które są wyświetlane, gdy użytkownik tworzy element. Te techniki najczęściej są wykonywane w definicji DSL, a niektóre wymagają kilku wierszy kodu programu.

3.  Rozszerzanie narzędzi do modelowania przy użyciu kodu programu. VMSDK jest zaprojektowany specjalnie w celu ułatwiają integrowanie rozszerzeń z kodem, który jest generowany na podstawie definicji DSL.  Aby uzyskać więcej informacji, zobacz [pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
>  Po zaktualizowaniu pliku definicji DSL, nie zapomnij kliknąć **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań, przed ponowną kompilację rozwiązania.

## <a name="customShapes"></a> W tej sekcji

|Aby uzyskać ten efekt|Można znaleźć w tym temacie|
|-|-|
|Zezwalaj użytkownikowi na Ustawianie kolorów i styl właściwości kształtu.|Kliknij prawym przyciskiem myszy klasę kształtu lub połączenia, wskaż opcję **Dodaj udostępniane**i kliknij element.<br /><br /> Zobacz [Dostosowywanie prezentacji na diagramie](../modeling/customizing-presentation-on-the-diagram.md).|
|Różne rodzaje elementu modelu podobne na diagramie, udostępnianie właściwości, takie jak początkowa wysokość i szerokość, kolory, etykietki narzędzi.|Za pomocą dziedziczenia między kształty lub klas łącznika. Mapowania między pochodnej kształty i klasy pochodnej domeny dziedziczą szczegóły mapowania elementów nadrzędnych.<br /><br /> Lub mapowania klas innej domeny w tej samej klasie kształtu.|
|Klasa elementu modelu jest wyświetlana w kontekstach różne kształty.|Więcej niż jedną klasę kształtu są mapowane na tej samej klasy domeny. W przypadku tworzenia rozwiązania, postępuj zgodnie z raportu o błędach i podaj żądany kod, aby zdecydować, jaki kształt do użycia.|
|Kolor kształtu lub inne funkcje, takie jak czcionki wskazuje bieżący stan.|Zobacz [aktualizowanie kształtów i łączników, aby odzwierciedlały Model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Utwórz regułę, która aktualizuje właściwości narażone. Zobacz [reguły propagujące zmiany w modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Możesz też użyć OnAssociatedPropertyChanged() można zaktualizować — dostępne funkcje, takie jak czcionki lub link strzałki.|
|Ikona na zmiany kształtu do wskazywania stanu.|Ustaw widoczność mapowanie dekoratora w oknie Szczegóły języka DSL. Znajdź kilka dekoratory obrazu na tym samym położeniu. Zobacz [aktualizowanie kształtów i łączników, aby odzwierciedlały Model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Lub Zastąp `ImageField.GetDisplayImage()`. Zobacz przykład w <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|
|Ustawienie obrazu tła na żaden kształt|Zastąpienie InitializeInstanceResources(), aby dodać zakotwiczonej ImageField. Zobacz [Dostosowywanie prezentacji na diagramie](../modeling/customizing-presentation-on-the-diagram.md).|
|Zagnieżdżanie kształtów na dowolnym poziomie|Skonfiguruj cykliczne, osadzanie drzewa. Zdefiniuj boundsrules — zawiera kształty. Zobacz [Dostosowywanie prezentacji na diagramie](../modeling/customizing-presentation-on-the-diagram.md).|
|Dołącz łączników w stałym punktach na krawędzi elementu.|Zdefiniuj osadzone elementy terminala, reprezentowane przez małe porty na diagramie. Boundsrules — umożliwiają rozwiązywanie porty w miejscu. Zobacz przykład schemat w [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|
|Pole tekstowe wyświetla wartość pochodzi od innych wartości.|Mapowanie dekoratora tekstu do właściwości domeny obliczeniowe lub magazynu niestandardowego. Aby uzyskać więcej informacji, zobacz [obliczeniowe i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md).|
|Propagowanie zmian między elementami modelu lub między kształtami|Zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).|
|Propagujące zmiany do zasobów takich jak inne rozszerzenia programu Visual Studio spoza sklepu.|Zobacz [programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Okno właściwości wyświetla właściwości powiązanych elementów.|Skonfiguruj właściwości przekazywania. Zobacz [Dostosowywanie okna właściwości](../modeling/customizing-the-properties-window.md).|
|Kategorie właściwości|W oknie właściwości jest podzielony na sekcje o nazwie kategorie. Ustaw **kategorii** właściwości usługi domeny. Właściwości o takiej samej nazwie kategorii będą wyświetlane w tej samej sekcji. Można również ustawić **kategorii** roli relacji.|
|Kontrola dostępu użytkownika do właściwości domeny|Ustaw **jest możliwa do przeglądania** wartość false, aby uniemożliwić właściwości domeny w oknie dialogowym właściwości w czasie wykonywania. Można nadal mapować do dekoratorów tekstu.<br /><br /> **Jest tylko do odczytu interfejsu użytkownika** uniemożliwia użytkownikom zmianę właściwości domeny.<br /><br /> Nie wpływa na dostęp do programu do właściwości domeny.|
|Zmień nazwę, ikonę i widoczność węzły w Eksploratorze modelu DSL.|Zobacz [Dostosowywanie Eksploratora modelu](../modeling/customizing-the-model-explorer.md).|
|Włącz kopiowanie, wycinanie i wklejanie|Ustaw **Włącz kopiowanie wklejanie** właściwość **edytora** węzła w Eksploratorze DSL.|
|Kopiuj odwołanie łącza i ich celów zawsze wtedy, gdy element zostanie skopiowany. Na przykład skopiuj komentarze dołączone do elementu.|Ustaw **propaguje kopiowania** własności dla roli źródłowej (reprezentowane przez wiersz po jednej stronie relacji domeny w diagramem definicji DSL).<br /><br /> Pisanie kodu w celu zastąpienia ProcessOnCopy, aby osiągnąć bardziej złożonych efekty.<br /><br /> Zobacz [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md).|
|Usunąć, zmienić elementu nadrzędnego lub Połącz ponownie powiązanych elementów, gdy element zostanie usunięty.|Ustaw **propaguje Usuń** wartość rolę w relacji. Dla bardziej złożonych efektów zastąpić `ShouldVisitRelationship` i `ShouldVisitRolePlayer` metody `MyDslDeleteClosure` klasy zdefiniowane w **DomainModel.cs**<br /><br /> Zobacz [Dostosowywanie zachowania dotyczącego usuwania](../modeling/customizing-deletion-behavior.md)|
|Zachowaj kształt układ i wygląd na kopiowanie i przeciąganie i upuszczanie.|Dodawanie kształtów i łączników do skopiowanych `ElementGroupPrototype`. To najwygodniejsza metody do przesłonięcia `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Zobacz [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md).|
|Wklejanie kształtów w wybranej lokalizacji, na przykład w bieżącej pozycji kursora.|Zastąp `ClipboardCommandSet.ProcessOnCopy()` użyć lokalizacji określonej wersji `ElementOperations.Merge().` zobacz [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md).|
|Tworzyć linki do dodatkowych przy wklejaniu|Zastąp ClipboardCommandSet.ProcessOnPasteCommand()|
|Przeciągania i upuszczania, z tym diagramie z innymi językami DSL i Windows, elementy|Zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Zezwalaj na kształt lub narzędziu można przeciągać kształt podrzędny, taki jak port, tak, jakby były przeciągnięto element nadrzędny.|Zdefiniuj dyrektywa scalania elementów na klasę obiektu docelowego do przekazywania upuszczony obiekt do elementu nadrzędnego. Zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).|
|Zezwalaj na kształcie lub narzędzia można przeciągać kształt i linki do dodatkowych lub obiekty utworzone. Na przykład, aby zezwolić na komentarz, aby być upuszczone na element, do której ma być połączone.|Zdefiniuj dyrektywa scalania elementów dla klasy domeny docelowej i definiują łącza do wygenerowania. W przypadku złożonych można dodać kod niestandardowy. Zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).|
|Utwórz grupę elementów za pomocą jednego narzędzia. Na przykład składnik ustalony zestawu portów.|Zastąp metodę inicjowania przybornika w ToolboxHelper.cs. Utwórz Element grupy prototyp (EGP) zawierający elementy i ich łącza relacji. Zobacz [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Objęte kształty głównej i port EGP albo zdefiniuj boundsrules — do pozycji kształtów portu podczas tworzenia wystąpienia EGP. Zobacz [boundsrules — ograniczenie lokalizacji i rozmiaru kształtu](../modeling/boundsrules-constrain-shape-location-and-size.md).|
|Używanie narzędzia połączenia z jednego do utworzenia wystąpienia kilka typów relacji.|Dodaj łącze połączyć dyrektywy LCD do konstruktora połączeń, które jest wywoływane przez narzędzie. LCD określenia typu relacji z typów dwóch elementów. Aby to zależą od stany elementów, można dodać kod niestandardowy. Zobacz [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md).|
|Umocowany narzędzia — użytkownik może kliknąć dwukrotnie dowolne narzędzie do tworzenia wielu kształtów i łączników pod rząd.|Eksplorator modelu DSL wybierz `Editor` węzła. W oknie właściwości ustaw **używa elementów przybornika umocowany**.|
|Definiowanie polecenia menu|Zobacz [jak: Modyfikowanie standardowego polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Ograniczenie modelu przy użyciu reguł sprawdzania poprawności|Zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md)|
|Generowanie kodu, plików konfiguracji lub dokumentów z języka DSL.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Dostosowywanie sposobu zapisywania modeli do pliku.|Zobacz [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Zapisz modeli do baz danych lub innego nośnika.|Zastąp *YourLanguage*DocData<br /><br /> Zobacz [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integracja wielu języków DSL, aby mogły działać w ramach jednej aplikacji.|Zobacz [integrowanie modeli za pomocą programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Zezwalaj DSL być rozszerzony przez strony trzecie i kontrolować rozszerzenia.|[Rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Udostępnianie klas między językami DSL za pomocą biblioteki DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]