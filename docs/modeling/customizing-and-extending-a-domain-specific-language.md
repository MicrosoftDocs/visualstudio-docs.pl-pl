---
title: Dostosowywanie i rozszerzanie języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9040e65d3e9acce101ee6b481c2cd27d24285169
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597168"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Dostosowywanie i poszerzanie języka specyficznego dla domeny

Zestaw SDK programu Visual Studio Modeling and wizualizacji (VMSDK) udostępnia kilka poziomów, na których można zdefiniować narzędzia modelowania:

1. Definiowanie języka specyficznego dla domeny (DSL) przy użyciu diagramu definicji DSL. Można szybko utworzyć DSL z notacją diagramowy, czytelną postać XML i podstawowymi narzędziami, które są wymagane do generowania kodu i innych artefaktów. Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

2. Dostosuj DSL przy użyciu bardziej zaawansowanych funkcji definicji DSL. Na przykład można utworzyć dodatkowe linki, gdy użytkownik tworzy element. Te techniki są głównie osiągane w definicji DSL, a niektóre wymagają kilku wierszy kodu programu.

3. Rozszerzając narzędzia modelowania przy użyciu kodu programu. VMSDK został zaprojektowany specjalnie w celu ułatwienia integracji rozszerzeń z kodem, który jest generowany na podstawie definicji DSL. Aby uzyskać więcej informacji, zobacz [pisanie kodu w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Po zaktualizowaniu pliku definicji DSL nie zapomnij kliknąć przycisk **Przekształć wszystkie szablony** na pasku narzędzi **Eksplorator rozwiązań** przed odbudowaniem rozwiązania.

## <a name="article-reference"></a>Dokumentacja artykułu

|Aby osiągnąć ten efekt|Zapoznaj się z tym tematem|
|-|-|
|Zezwalaj użytkownikowi na ustawianie właściwości koloru i stylu kształtu.|Kliknij prawym przyciskiem myszy klasę kształtu lub łącznika, wskaż polecenie **Dodaj uwidocznione**i kliknij element.|
|Różne klasy elementu modelu wyglądają podobnie na diagramie, udostępniając właściwości, takie jak początkowa wysokość i szerokość, kolor i etykietki narzędzi.|Używaj dziedziczenia między kształtami lub klasami łączników. Mapowania między pochodnymi i pochodnymi klasami domeny dziedziczą szczegóły mapowania elementów nadrzędnych.<br /><br /> Lub Mapuj różne klasy domeny do tej samej klasy kształtu.|
|Klasa elementu modelu jest wyświetlana przez różne konteksty kształtów.|Mapuj więcej niż jedną klasę kształtu do tej samej klasy domeny. Podczas kompilowania rozwiązania postępuj zgodnie z raportem o błędach i podaj żądany kod, aby zdecydować, którego kształtu użyć.|
|Kolor kształtu lub inne funkcje, takie jak Font, wskazują bieżący stan.|Zobacz [Aktualizowanie kształtów i łączników, aby odzwierciedlały model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Utwórz regułę, która aktualizuje uwidocznione właściwości. Zobacz [reguły propagują zmiany w modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Lub użyj OnAssociatedPropertyChanged (), aby zaktualizować nieuwidocznione funkcje, takie jak strzałki łącza lub czcionki.|
|Ikona zmiany kształtu wskazująca stan.|Ustaw widoczność mapowania dekoratora w oknie Szczegóły DSL. Znajdź kilka dekoratory obrazów w tym samym położeniu. Zobacz [Aktualizowanie kształtów i łączników, aby odzwierciedlały model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Lub Zastąp `ImageField.GetDisplayImage()`. Zobacz przykład w <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|
|Ustaw obraz tła na dowolnym kształcie|Zastąp InitializeInstanceResources (), aby dodać kotwicę ImageField.|
|Zagnieżdżanie kształtów do dowolnej głębokości|Skonfiguruj cykliczne drzewo osadzania. Zdefiniuj BoundsRules — tak, aby zawierały kształty.|
|Dołącz łączniki dla stałych punktów na granicy elementu.|Zdefiniuj osadzone elementy terminalu reprezentowane przez małe porty na diagramie. Użyj BoundsRules —, aby naprawić porty w miejscu. Zobacz przykład diagramu obwodowego w temacie [Wizualizacja i modelowanie SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).|
|Pole tekstowe wyświetla wartość pochodną od innych wartości.|Zamapuj tekst dekoratora na Właściwość obliczeniową lub niestandardową domeny magazynu. Aby uzyskać więcej informacji, zobacz [obliczeniowe i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md).|
|Propagowanie zmian między elementami modelu lub między kształtami|Zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md).|
|Propagowanie zmian do zasobów, takich jak inne rozszerzenia programu Visual Studio, poza sklepem.|Zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|W oknie właściwości są wyświetlane właściwości powiązanego elementu.|Skonfiguruj przekazywanie właściwości. Zobacz [Dostosowywanie okna właściwości](../modeling/customizing-the-properties-window.md).|
|Kategorie właściwości|Okno właściwości jest podzielone na sekcje o nazwie kategorie. Ustaw **kategorię** właściwości domeny. Właściwości o tej samej nazwie kategorii będą wyświetlane w tej samej sekcji. Można również ustawić **kategorię** roli relacji.|
|Kontrolowanie dostępu użytkowników do właściwości domeny|Ustaw wartość **umożliwia przeglądania** false, aby zapobiec wyświetlaniu właściwości domeny w okno właściwości w czasie wykonywania. Nadal można mapować na dekoratory tekstu.<br /><br /> **Jest interfejsem użytkownika tylko do odczytu** uniemożliwia użytkownikom zmianę właściwości domeny.<br /><br /> Nie ma to oddziaływania na dostęp do właściwości domeny.|
|Zmień nazwę, ikonę i widoczność węzłów w Eksploratorze modelu DSL.|Zobacz [Dostosowywanie Eksploratora modelu](../modeling/customizing-the-model-explorer.md).|
|Włącz kopiowanie, wycinanie i wklejanie|Ustaw właściwość **Włącz kopiowanie wklejenia** węzła **Edytor** w Eksploratorze DSL.|
|Kopiuj linki odwołań i ich obiekty docelowe za każdym razem, gdy element jest kopiowany. Na przykład skopiuj Komentarze dołączone do elementu.|Ustaw właściwość **propagowania kopii** roli źródłowej (reprezentowanej przez wiersz po jednej stronie relacji domeny na DIAGRAMIE definicji DSL).<br /><br /> Napisz kod, aby przesłonić ProcessOnCopy w celu uzyskania bardziej złożonych efektów.<br /><br /> Zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).|
|Usuń, Zmień element nadrzędny lub Połącz ponownie powiązane elementy po usunięciu elementu.|Ustaw wartość opcji **Usuń propagacje** roli relacji. W przypadku bardziej złożonych efektów Zastąp metody `ShouldVisitRelationship` i `ShouldVisitRolePlayer` w klasie `MyDslDeleteClosure` zdefiniowanej w **DomainModel.cs**.|
|Zachowanie układu kształtu i wyglądu przy kopiowaniu i przeciąganiu.|Dodaj kształty i łączniki do skopiowanego `ElementGroupPrototype`. Najbardziej wygodną metodą przesłonięcia jest `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).|
|Wklej kształty w wybranej lokalizacji, na przykład w bieżącym położeniu kursora.|Zastąp `ClipboardCommandSet.ProcessOnCopy()`, aby użyć wersji `ElementOperations.Merge().` określonej dla lokalizacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).|
|Utwórz dodatkowe linki przy wklejaniu|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|Włącz przeciąganie i upuszczanie z tego diagramu, inne językami DSL i elementy systemu Windows|Zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Umożliwia przeciągnięcie kształtu lub narzędzia do kształtu podrzędnego, takiego jak port, tak jakby był przeciągany do elementu nadrzędnego.|Zdefiniuj dyrektywę scalania elementów w klasie obiektu docelowego, aby przesłać do przodu usunięty obiekt do elementu nadrzędnego. Zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).|
|Umożliwia przeciągnięcie kształtu lub narzędzia do kształtu i dodanie dodatkowych linków lub obiektów. Na przykład, aby zezwolić na porzucenie komentarza do elementu, do którego ma być ono połączone.|Zdefiniuj dyrektywę scalenia elementów w klasie domeny docelowej i zdefiniuj linki do wygenerowania. W złożonych przypadkach można dodać kod niestandardowy. Zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).|
|Utwórz grupę elementów za pomocą jednego narzędzia. Na przykład składnik ze stałym zestawem portów.|Zastąp metodę inicjowania przybornika w ToolboxHelper.cs. Utwórz prototyp grupy elementów (EGP) zawierający elementy i ich linki relacji. Zobacz [Dostosowywanie narzędzi i Przybornik](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Uwzględnij jednostki główne i kształty portów w EGP lub Zdefiniuj BoundsRules —, aby pozycjonować kształty portów podczas tworzenia wystąpienia EGP.|
|Użyj jednego z narzędzi połączenia, aby utworzyć wystąpienie kilku typów relacji.|Dodaj dyrektywy łączenia linków (LCD) do konstruktora połączeń, który jest wywoływany przez narzędzie. LCDs określa typ relacji z typów dwóch elementów. Aby to uczynić zależeć od Stanów elementów, można dodać kod niestandardowy. Zobacz [Dostosowywanie narzędzi i Przybornik](../modeling/customizing-tools-and-the-toolbox.md).|
|Narzędzia Sticky Notes — użytkownik może dwukrotnie kliknąć dowolne narzędzie, aby utworzyć wiele kształtów lub łączników.|W Eksploratorze DSL wybierz węzeł `Editor`. W okno Właściwości, ustaw opcję **używa elementów przybornika programu Sticky**.|
|Definiowanie poleceń menu|Zobacz [jak: modyfikowanie standardowego polecenia menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Ograniczanie modelu przy użyciu reguł walidacji|Zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)|
|Generuj kod, pliki konfiguracyjne lub dokumenty z poziomu języka DSL.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Dostosuj sposób zapisywania modeli w pliku.|Zobacz [dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Zapisuj modele w bazach danych lub na innych nośnikach.|Zastąp *YourLanguage*DocData<br /><br /> Zobacz [dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integruj kilka językami DSL, aby działały jako część jednej aplikacji.|Zobacz [integrowanie modeli za pomocą programu Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Zezwalaj na Rozszerzanie DSL przez inne osoby i kontroluj rozszerzenie.|[Rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Udostępnianie klas między językami DSL za pomocą biblioteki DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Pisanie kodu w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
