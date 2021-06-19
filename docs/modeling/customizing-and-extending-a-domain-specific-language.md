---
title: Dostosowywanie i rozszerzanie języka specyficznego dla domeny
description: Dowiedz się, w jaki Visual Studio SDK modelowania i wizualizacji (VMSDK) zapewnia kilka poziomów, na których można zdefiniować narzędzia do modelowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389387"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Dostosowywanie i rozszerzanie języka specyficznego dla domeny

Visual Studio Modelowanie i wizualizacja SDK (VMSDK) oferuje kilka poziomów, na których można zdefiniować narzędzia do modelowania:

1. Zdefiniuj język specyficzny dla domeny (DSL) przy użyciu diagramu definicji DSL. Możesz szybko utworzyć DSL z notacją diagramu, czytelnym formularzem XML i podstawowymi narzędziami wymaganymi do generowania kodu i innych artefaktów. Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

2. Dostosuj DSL przy użyciu bardziej zaawansowanych funkcji definicji DSL. Na przykład dodatkowe linki mogą być wyświetlane, gdy użytkownik tworzy element. Te techniki są w większości osiągane w definicji DSL, a niektóre wymagają kilku wierszy kodu programu.

3. Rozszerzanie narzędzi modelowania przy użyciu kodu programu. VmSDK zaprojektowano specjalnie, aby ułatwić integrowanie rozszerzeń z kodem generowanym na podstawie definicji DSL. Aby uzyskać więcej informacji, zobacz Writing Code to Customize a Domain-Specific Language (Pisanie kodu [w celu dostosowania Domain-Specific języku ).](../modeling/writing-code-to-customise-a-domain-specific-language.md)

> [!NOTE]
> Po zaktualizowaniu pliku definicji DSL nie zapomnij  kliknąć przycisku Przekształć wszystkie szablony na pasku narzędzi Eksplorator rozwiązań **przed** przebudową rozwiązania.

## <a name="article-reference"></a>Informacje o artykule

|Aby osiągnąć ten efekt|Zapoznaj się z tym tematem|
|-|-|
|Zezwala użytkownikowi na ustawianie właściwości koloru i stylu kształtu.|Kliknij prawym przyciskiem myszy klasę kształtu lub łącznika, wskaż polecenie **Dodaj ujawnione** i kliknij element.|
|Różne klasy elementu modelu wyglądają podobnie na diagramie, udostępniając właściwości, takie jak początkowa wysokość i szerokość, kolor i etykietki narzędzi.|Użyj dziedziczenia między kształtami lub klasami łączników. Mapowania między kształtami pochodnymi i klasami domeny pochodnej dziedziczą szczegóły mapowania rodziców.<br /><br /> Możesz też zamapować różne klasy domen na tę samą klasę kształtu.|
|Klasa elementu modelu jest wyświetlana przez konteksty o różnych kształtach.|Mapuj więcej niż jedną klasę kształtu na tę samą klasę domeny. Podczas tworzenia rozwiązania postępuj zgodnie z raportem o błędach i podaj żądany kod, aby zdecydować, jakiego kształtu użyć.|
|Kolor kształtu lub inne funkcje, takie jak czcionka, wskazują bieżący stan.|Zobacz [Aktualizowanie kształtów i łączników w celu odzwierciedlenia modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Utwórz regułę, która aktualizuje widoczne właściwości. Zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Możesz też użyć funkcji OnAssociatedPropertyChanged(), aby zaktualizować nieuświetlone funkcje, takie jak strzałki linku lub czcionka.|
|Ikona zmiany kształtu w celu wskazania stanu.|Ustaw widoczność mapowania dekoratora w oknie Szczegóły DSL. Znajdź kilka dekoratorów obrazów w tej samej pozycji. Zobacz  [Aktualizowanie kształtów i łączników w celu odzwierciedlenia modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Możesz też przesłonić `ImageField.GetDisplayImage()` . Zobacz przykład w <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Ustawianie obrazu tła dla dowolnego kształtu|Zastąp element InitializeInstanceResources(), aby dodać zakotwiczony element ImageField.|
|Zagnieżdżanie kształtów na dowolnej głębokości|Skonfiguruj cykliczne drzewo osadzania. Zdefiniuj elementy BoundsRules, aby zawierały kształty.|
|Dołączanie łączników w stałych punktach na granicy elementu.|Zdefiniuj osadzone elementy terminalu reprezentowane przez małe porty na diagramie. Użyj funkcji BoundsRules, aby naprawić porty. Zobacz przykładowy diagram obwodu w [te tematze Visualization and Modeling SDK (Zestaw SDK wizualizacji i modelowania).](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|
|Pole tekstowe wyświetla wartość pochodną innych wartości.|Zamapuj dekorator tekstu na właściwość domeny Calculated lub Custom Storage. Aby uzyskać więcej informacji, zobacz [Właściwości magazynu obliczeniowego i niestandardowego.](../modeling/calculated-and-custom-storage-properties.md)|
|Propagacja zmian między elementami modelu lub między kształtami|Zobacz [Validation in a Domain-Specific Language (Walidacja w Domain-Specific języku).](../modeling/validation-in-a-domain-specific-language.md)|
|Propagacja zmian do zasobów, takich jak Visual Studio rozszerzenia poza magazynem.|Zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Okno właściwości wyświetla właściwości powiązanego elementu.|Konfigurowanie przekazywania właściwości. Zobacz [Dostosowywanie okna właściwości](../modeling/customizing-the-properties-window.md).|
|Kategorie właściwości|Okno właściwości jest podzielone na sekcje nazywane kategoriami. Ustaw **kategorię** właściwości domeny. Właściwości o tej samej nazwie kategorii będą wyświetlane w tej samej sekcji. Można również ustawić **kategorię** roli relacji.|
|Kontrolowanie dostępu użytkownika do właściwości domeny|Ustaw **wartość fałszu** przeglądania, aby uniemożliwić pojawianie się właściwości domeny w okno Właściwości w czasie uruchamiania. Nadal można mapować go na dekoratory tekstu.<br /><br /> **Jest tylko do odczytu interfejsu** użytkownika uniemożliwia użytkownikom zmienianie właściwości domeny.<br /><br /> Nie ma to wpływu na dostęp programu do właściwości domeny.|
|Zmień nazwę, ikonę i widoczność węzłów w eksploratorze modeli DSL.|Zobacz [Dostosowywanie Eksploratora modelu.](../modeling/customizing-the-model-explorer.md)|
|Włączanie kopiowania, wycinania i wklejania|Ustaw właściwość **Enable Copy Paste węzła** **Edytor** w Eksploratorze DSL.|
|Kopiuj linki odwołania i ich elementy docelowe za każdym razem, gdy element jest kopiowany. Na przykład skopiuj komentarze dołączone do elementu.|Ustaw właściwość **Propagates Copy** roli źródłowej (reprezentowanej przez wiersz po jednej stronie relacji domeny na diagramie definicji DSL).<br /><br /> Napisz kod zastępujący metodę ProcessOnCopy, aby uzyskać bardziej złożone efekty.<br /><br /> Zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).|
|Usuwanie, ponowne łączenie lub ponowne łączenie powiązanych elementów po usunięciu elementu.|Ustaw wartość **Propagacja usuwania** roli relacji. Aby uzyskać bardziej złożone efekty, przesłoń `ShouldVisitRelationship` metody i w klasie zdefiniowane w klasie `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel.cs**.|
|Zachowaj układ i wygląd kształtu podczas kopiowania i przeciągania i upuszczania.|Dodaj kształty i łączniki do skopiowanego pliku `ElementGroupPrototype` . Najbardziej wygodną metodą przesłonięcia jest `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).|
|Wklej kształty w wybranej lokalizacji, na przykład bieżące położenie kursora.|Zastąp `ClipboardCommandSet.ProcessOnCopy()` , aby użyć specyficznej dla lokalizacji wersji zobacz Dostosowywanie zachowania `ElementOperations.Merge().` [kopiowania](../modeling/customizing-copy-behavior.md).|
|Tworzenie dodatkowych linków podczas wklejania|Zastąp schowekCommandSet.ProcessOnPasteCommand()|
|Włączanie przeciągania i upuszczania z tego diagramu, innych plików DSL i elementów systemu Windows|Zobacz [How to: Add a Drag-and-Drop Handler (Jak dodać program obsługi przeciągania i upuszczania)](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Zezwalaj na przeciągnięcie kształtu lub narzędzia na kształt podrzędny, taki jak port, tak jakby został przeciągnięty do elementu nadrzędnego.|Zdefiniuj dyrektywę scalania elementów w klasie obiektu docelowego, aby przesyłać porzucony obiekt do obiektu nadrzędnego. Zobacz [Dostosowywanie tworzenia i przemieszczania elementów](../modeling/customizing-element-creation-and-movement.md).|
|Zezwalaj na przeciągnięcie kształtu lub narzędzia na kształt i mieć utworzone dodatkowe linki lub obiekty. Na przykład, aby zezwolić na porzucanie komentarza do elementu, z którym ma zostać połączony.|Zdefiniuj dyrektywę scalania elementów w docelowej klasie domeny i zdefiniuj linki do wygenerowania. W złożonych przypadkach można dodać kod niestandardowy. Zobacz [Dostosowywanie tworzenia i przemieszczania elementów](../modeling/customizing-element-creation-and-movement.md).|
|Utwórz grupę elementów za pomocą jednego narzędzia. Na przykład składnik ze stałym zestawem portów.|Zastąp metodę inicjowania przybornika w przybornikuHelper.cs. Utwórz prototyp grupy elementów (EGP) zawierający elementy i ich linki relacji. Zobacz [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Uwzględnij kształty jednostki i portu w EGP lub zdefiniuj jednostki BoundsRules, aby ustawić położenie kształtów portów podczas wystąpienia EGP.|
|Użyj jednego narzędzia połączenia, aby utworzyć wystąpienia kilku typów relacji.|Dodaj dyrektywy CONNECT (Link Connect Directives) do konstruktora połączeń wywoływanego przez narzędzie. Identyfikatory LCD określają typ relacji na podstawie typów dwóch elementów. Aby to zależeć od stanów elementów, możesz dodać kod niestandardowy. Zobacz [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md).|
|Narzędzia sticky — użytkownik może kliknąć dwukrotnie dowolne narzędzie, aby utworzyć kolejno wiele kształtów lub łączników.|W Eksploratorze DSL wybierz `Editor` węzeł. W okno Właściwości ustaw wartość Uses Sticky Toolbox Items (Używa **elementów przybornika sticky).**|
|Definiowanie poleceń menu|Zobacz [How to: Modify a Standard Menu Command ( How to: Modify a Standard Menu Command)](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Ograniczanie modelu przy użyciu reguł weryfikacji|Zobacz [Validation in a Domain-Specific Language (Sprawdzanie poprawności w Domain-Specific języku)](../modeling/validation-in-a-domain-specific-language.md)|
|Generowanie kodu, pliki konfiguracji lub dokumenty z DSL.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Dostosowywanie sposobu zapisania modeli w pliku.|Zobacz [Dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Zapisywanie modeli w bazach danych lub na innych nośnikach.|Zastąp *yourLanguage* DocData<br /><br /> Zobacz [Dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Zintegruj kilka plików DSL, aby działały w ramach jednej aplikacji.|Zobacz [Integrating Models by using Visual Studio Modelbus (Integrowanie modeli przy użyciu Visual Studio Modelbus).](../modeling/integrating-models-by-using-visual-studio-modelbus.md)|
|Zezwalaj na rozszerzenie DSL przez inne firmy i kontrolować rozszerzenie.|[Rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Udostępnianie klas między językami DSL za pomocą biblioteki DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Pisanie kodu w celu dostosowania Domain-Specific językowego](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
