---
title: Dostosowywanie tworzenia i przesuwania elementów
description: Dowiedz się, jak zezwolić na przeciąganie elementu do innego elementu z przybornika albo operacji wklejania lub przenoszenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42339c532db3442d5fb5c5da3b51d94801a0907d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389400"
---
# <a name="customizing-element-creation-and-movement"></a>Dostosowywanie tworzenia i przesuwania elementów

Możesz zezwolić na przeciągnięcie elementu do innego elementu z przybornika albo w operacji wklejania lub przenoszenia. Przeniesione elementy mogą być połączone z elementami docelowymi przy użyciu poszczególnych relacji.

Dyrektywa scalania elementów (EMD) określa, co się stanie, gdy jeden element modelu zostanie *scalony* z innym elementem modelu. Dzieje się tak w następujących sytuacjach:

- Użytkownik przeciąga element z przybornika na diagram lub kształt.

- Użytkownik tworzy element przy użyciu menu Dodaj w eksploratorze lub kształtu przedziału.

- Użytkownik przenosi element z jednego toru do innego.

- Użytkownik wkleja element .

- Kod programu wywołuje dyrektywę scalania elementu.

Mimo że operacje tworzenia mogą się różnić od operacji kopiowania, w rzeczywistości działają w taki sam sposób. Gdy element jest dodawany, na przykład z przybornika, jego prototyp jest replikowany. Prototyp jest scalony z modelem w taki sam sposób, jak elementy, które zostały skopiowane z innej części modelu.

Odpowiedzialność za usługę EMD spoczywa na podjęciu decyzji o tym, jak obiekt lub grupa obiektów powinny być scalane w określonej lokalizacji w modelu. W szczególności decyduje o tym, jakie relacje powinny zostać połączone w celu połączenia scalonej grupy z modelem. Można również dostosować go, aby ustawić właściwości i utworzyć dodatkowe obiekty.

![Diagram przedstawiający element przed i po przyjrzeniu się drzewu elementów i ich relacjom odwoływać się, gdy E M D określa, jak nowy element jest dodawany.](../modeling/media/dsl-emd_merge.png)

EMD jest generowany automatycznie podczas definiowania relacji osadzania. Ten domyślny model EMD tworzy wystąpienie relacji, gdy użytkownicy dodają nowe wystąpienia podrzędne do elementu nadrzędnego. Te domyślne identyfikatory EMD można modyfikować, na przykład dodając kod niestandardowy.

Możesz również dodać własne identyfikatory EMD w definicji DSL, aby pozwolić użytkownikom przeciągać lub wklejać różne kombinacje scalonych i odbierających klas.

## <a name="defining-an-element-merge-directive"></a>Definiowanie dyrektywy scalania elementów

Dyrektywy scalania elementów można dodawać do klas domen, relacji domeny, kształtów, łączników i diagramów. Można je dodać lub znaleźć w Eksploratorze DSL w klasie domeny odbieracej. Klasa odbierający jest klasą domeny elementu, który jest już w modelu i z którym zostanie scalony nowy lub skopiowany element.

![Zrzut ekranu eksploratora DSL przedstawiający element E M D dodawany z elementem ExampleElement wybranym jako klasa indeksowania i zaznaczoną opcją Dotyczy podklas.](../modeling/media/dsl-emd_details.png)

Klasa **indeksowania to** klasa domeny elementów, które można scalić z składowymi klasy odbierającej. Wystąpienia podklas klasy indeksowania również zostaną scalone przez ten zestaw EMD, chyba że ustawisz dla podklas wartość False. 

Istnieją dwa rodzaje dyrektyw scalania:

- Dyrektywa **Scalanie** procesów określa relacje, za pomocą których nowy element powinien zostać połączony z drzewem.

- Dyrektywa **scalania** do przodu przekierowuje nowy element do innego elementu odbieraącego, zazwyczaj nadrzędnego.

Możesz dodać kod niestandardowy do dyrektyw scalania:

- Ustawienie **Używa niestandardowego akceptowania,** aby dodać własny kod, aby określić, czy konkretne wystąpienie elementu indeksowania powinno zostać scalone z elementem docelowym. Gdy użytkownik przeciągnie z przybornika, wskaźnik "nieprawidłowy" pokazuje, czy kod nie zezwala na scalanie.

   Na przykład można zezwolić na scalanie tylko wtedy, gdy element odbierający jest w określonym stanie.

- Ustawienie **Używa scalania niestandardowego** w celu dodania własnego kodu w celu zdefiniowania zmian wprowadzonych w modelu podczas scalania.

   Na przykład można ustawić właściwości w scalanym elemencie przy użyciu danych z jego nowej lokalizacji w modelu.

> [!NOTE]
> Jeśli napiszesz niestandardowy kod scalania, będzie on dotyczył tylko scalania, które są wykonywane przy użyciu tego rozwiązania EMD. Jeśli istnieją inne EMD, które scalają ten sam typ obiektu lub jeśli istnieje inny kod niestandardowy, który tworzy te obiekty bez użycia EMD, niestandardowy kod scalania nie będzie na nie mieć wpływu.
>
> Jeśli chcesz upewnić się, że nowy element lub nowa relacja są zawsze przetwarzane przez kod niestandardowy, rozważ zdefiniowanie elementu dla relacji osadzania i elementu w klasie `AddRule` `DeleteRule` domeny elementu. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Przykład: Definiowanie EMD bez kodu niestandardowego

Poniższy przykład umożliwia użytkownikom tworzenie elementu i łącznika w tym samym czasie przez przeciągnięcie z przybornika do istniejącego kształtu. W przykładzie dodano definicję EMD do definicji DSL. Przed wprowadzeniem tej modyfikacji użytkownicy mogą przeciągać narzędzia na diagram, ale nie na istniejące kształty.

Użytkownicy mogą również wklejać elementy do innych elementów.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Aby pozwolić użytkownikom na tworzenie elementu i łącznika w tym samym czasie

1. Utwórz nowy język DSL przy użyciu szablonu **rozwiązania w języku** minimalnym.

    Po uruchomieniu tego DSL, umożliwia tworzenie kształtów i łączników między kształtami. Nie można przeciągać nowego kształtu **ExampleElement** z przybornika do istniejącego kształtu.

2. Aby pozwolić użytkownikom scalać elementy `ExampleElement` na kształty, utwórz nowy element EMD w `ExampleElement` klasie domeny:

   1. W **Eksploratorze DSL** rozwiń **węzło klasy domen**. Kliknij prawym przyciskiem myszy, a następnie kliknij polecenie Add New Element Merge Directive (Dodaj `ExampleElement` **nową dyrektywę scalania elementów).**

   2. Upewnij się, że **okno Szczegóły DSL** jest otwarte, aby wyświetlić szczegóły nowego EMD. (Menu: **View**, **Other Windows**, DSL **Details**.)

3. Ustaw **klasę Indeksowanie w** oknie Szczegóły DSL, aby zdefiniować klasę elementów, które można scalić z `ExampleElement` obiektami.

    W tym przykładzie wybierz pozycję `ExampleElements` , aby użytkownik może przeciągać nowe elementy do istniejących elementów.

    Zwróć uwagę, że klasa Indeksowanie staje się nazwą EMD w eksploratorze DSL.

4. W **obszarze Scalanie procesów przez utworzenie linków** dodaj dwie ścieżki:

   - Jedna ścieżka łączy nowy element z modelem nadrzędnym. Wyrażenie path, które należy wprowadzić, przechodzi z istniejącego elementu do relacji osadzania z modelem nadrzędnym. Na koniec określa rolę w nowym linku, do którego zostanie przypisany nowy element. Ścieżka jest następująca:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - Druga ścieżka łączy nowy element z istniejącym elementem. Wyrażenie path określa relację odwołania i rolę, do której zostanie przypisany nowy element. Ta ścieżka jest następująca:

      `ExampleElementReferencesTargets.Sources`

      Każdą ścieżkę można utworzyć za pomocą narzędzia nawigacji po ścieżkach:

      1. W **obszarze Scalanie procesów przez utworzenie linków w ścieżkach** kliknij pozycję **\<add path>** .

      2. Kliknij strzałkę listy rozwijanej z prawej strony elementu listy. Zostanie wyświetlony widok drzewa.

      3. Rozwiń węzły w drzewie, aby określić ścieżkę.

5. Testowanie DSL:

   1. Naciśnij **klawisz F5,** aby ponownie skompilować i uruchomić rozwiązanie.

        Ponowne kompilowanie będzie trwać dłużej niż zwykle, ponieważ wygenerowany kod zostanie zaktualizowany z szablonów tekstowych, aby był zgodny z nową definicją DSL.

   2. Po wystąpieniu eksperymentalnym Visual Studio, otwórz plik modelu DSL. Utwórz kilka przykładowych elementów.

   3. Przeciągnij z narzędzia **Example Element** na istniejący kształt.

        Zostanie wyświetlony nowy kształt połączony z istniejącym kształtem za pomocą łącznika.

   4. Skopiuj istniejący kształt. Wybierz inny kształt i wklej go.

        Tworzona jest kopia pierwszego kształtu.  Ma nową nazwę i jest połączona z drugim kształtem za pomocą łącznika.

Zwróć uwagę na następujące kwestie w tej procedurze:

- Tworząc dyrektywy scalania elementów, można zezwolić dowolnej klasie elementu na akceptowanie innych. EMD jest tworzony w klasie domeny odbieracej, a akceptowana klasa domeny jest określona w **polu Klasa** indeksu.

- Definiując ścieżki, można określić, które linki mają być używane do łączenia nowego elementu z istniejącym modelem.

     Określone linki powinny zawierać jedną relację osadzania.

- Proces EMD ma wpływ zarówno na tworzenie z przybornika, jak i na operacje wklejania.

     Jeśli piszesz kod niestandardowy, który tworzy nowe elementy, możesz jawnie wywołać EMD przy użyciu `ElementOperations.Merge` metody . Dzięki temu kod łączy nowe elementy z modelem w taki sam sposób jak inne operacje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania.](../modeling/customizing-copy-behavior.md)

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Przykład: dodawanie niestandardowego kodu accept do rozwiązania EMD

Dodając kod niestandardowy do rozwiązania EMD, można zdefiniować bardziej złożone zachowanie scalania. Ten prosty przykład uniemożliwia użytkownikowi dodawanie do diagramu więcej niż stałej liczby elementów. W przykładzie zmodyfikowana jest domyślna EMD, która towarzyszy osadzaniu relacji.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Aby napisać niestandardowy kod akceptowania, aby ograniczyć to, co użytkownik może dodać

1. Utwórz DSL przy użyciu szablonu **rozwiązania w języku** minimalnym. Otwórz diagram definicji DSL.

2. W Eksploratorze DSL **rozwiń węzło klasy domen** `ExampleModel` , , dyrektywy **scalania elementów**. Wybierz dyrektywę scalania elementów o nazwie `ExampleElement` .

     Ten zestaw EMD kontroluje sposób, w jaki użytkownik może tworzyć nowe obiekty w modelu, na przykład `ExampleElement` przeciągając z przybornika.

3. W **oknie Szczegóły DSL** wybierz pozycję **Używa niestandardowego akceptowania**.

4. Ponownie skompiluj rozwiązanie. Będzie to trwać dłużej niż zwykle, ponieważ wygenerowany kod zostanie zaktualizowany z modelu.

     Zostanie zgłoszony błąd kompilacji podobny do: "Company.ElementMergeSample.ExampleElement does not contain a definition for CanMergeExampleElement..."

     Należy zaimplementować metodę `CanMergeExampleElement` .

5. Utwórz nowy plik kodu w **projekcie Dsl.** Zastąp jego zawartość poniższym kodem i zmień przestrzeń nazw na przestrzeń nazw projektu.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    Ten prosty przykład ogranicza liczbę elementów, które można scalić z modelem nadrzędnym. Aby uzyskać bardziej interesujące warunki, metoda może sprawdzić dowolne właściwości i linki obiektu odbieranego. Może również sprawdzać właściwości scalania elementów, które są przerzucane w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Aby uzyskać więcej informacji na temat `ElementGroupPrototypes` systemu , zobacz Dostosowywanie zachowania [kopiowania.](../modeling/customizing-copy-behavior.md) Aby uzyskać więcej informacji na temat pisania kodu, który odczytuje model, zobacz [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)(Nawigowanie po modelu i aktualizowanie go w kodzie programu).

6. Testowanie DSL:

    1. Naciśnij **klawisz F5,** aby ponownie skompilować rozwiązanie. Po otwarciu eksperymentalnego wystąpienia Visual Studio otwórz wystąpienie dsl.

    2. Utwórz nowe elementy na kilka sposobów:

        - Przeciągnij z narzędzia **Example Element** na diagram.

        - W **Eksploratorze modeli przykładów** kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij polecenie **Dodaj nowy przykładowy element**.

        - Skopiuj i wklej element na diagramie.

    3. Sprawdź, czy nie możesz użyć żadnego z tych sposobów, aby dodać więcej niż cztery elementy do modelu. Jest to spowodowane tym, że wszystkie używają dyrektywy Scalanie elementów.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Przykład: dodawanie niestandardowego kodu scalania do rozwiązania EMD

W niestandardowym kodzie scalania można zdefiniować, co się stanie, gdy użytkownik przeciągnie narzędzie lub wkleja element. Istnieją dwa sposoby definiowania scalania niestandardowego:

1. Ustaw **używa scalania niestandardowego** i podać wymagany kod. Kod zastępuje wygenerowany kod scalania. Użyj tej opcji, jeśli chcesz całkowicie ponownie zdefiniować sposób scalania.

2. Zastąp `MergeRelate` metodę i opcjonalnie `MergeDisconnect` metodę . W tym celu należy ustawić właściwość **Generuje podwójny pochodny** klasy domeny. Kod może wywołać wygenerowany kod scalania w klasie bazowej. Użyj tej opcji, jeśli chcesz wykonać dodatkowe operacje po zakończeniu scalania.

   Te podejścia mają wpływ tylko na scalania wykonywane przy użyciu tego rozwiązania EMD. Jeśli chcesz wpłynąć na wszystkie sposoby tworzenia scalonego elementu, alternatywą jest zdefiniowanie elementu w relacji osadzania i elementu w scalonej `AddRule` `DeleteRule` klasie domeny. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Aby zastąpić mergeRelate

1. W definicji DSL upewnij się, że zdefiniowano definicję EMD, do której chcesz dodać kod. Jeśli chcesz, możesz dodać ścieżki i zdefiniować niestandardowy kod akceptowania zgodnie z opisem w poprzednich sekcjach.

2. Na diagramie DslDefinition wybierz klasę odbieraną scalania. Zazwyczaj jest to klasa na końcu źródła relacji osadzania.

     Na przykład w języku DSL wygenerowanym na podstawie rozwiązania w języku minimalnym wybierz pozycję `ExampleModel` .

3. W **oknie Właściwości** ustaw wartość true  **dla właściwości Generates Double Derived (Generuje podwójne pochodne).**

4. Ponownie skompiluj rozwiązanie.

5. Sprawdź zawartość **pliku Dsl\Generated Files\DomainClasses.cs.** Wyszukaj metody o `MergeRelate` nazwach i sprawdź ich zawartość. Pomoże to napisać własne wersje.

6. W nowym pliku kodu napisz klasę częściową dla klasy odbieracej i zastąp `MergeRelate` metodę . Pamiętaj, aby wywołać metodę podstawową. Na przykład:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>Aby napisać niestandardowy kod scalania

1. W **pliku Dsl\Generated Code\DomainClasses.cs** sprawdź metody o nazwie `MergeRelate` . Te metody tworzą połączenia między nowym elementem i istniejącym modelem.

    Ponadto należy sprawdzić metody o nazwie `MergeDisconnect` . Te metody odłączą element od modelu, gdy ma zostać usunięty.

2. W **eksploratorze DSL** wybierz lub utwórz dyrektywę scalania elementów, którą chcesz dostosować. W **oknie Szczegóły DSL** ustaw wartość **Używa niestandardowego scalania.**

    Po skonfigurowaniu tej opcji opcje **Scalanie procesów** **i** Scalanie do przodu są ignorowane. Zamiast tego jest używany kod.

3. Ponownie skompiluj rozwiązanie. Trwa to dłużej niż zwykle, ponieważ wygenerowane pliki kodu zostaną zaktualizowane z modelu.

    Zostaną wyświetlone komunikaty o błędach. Kliknij dwukrotnie komunikaty o błędach, aby wyświetlić instrukcje w wygenerowanym kodzie. Te instrukcje proszą o dostarczenie dwóch metod: `MergeRelate` *YourDomainClass* `MergeDisconnect` *i YourDomainClass*

4. Napisz metody w definicji klasy częściowej w oddzielnym pliku kodu. Przykłady, które zbadano wcześniej, powinny sugerować, czego potrzebujesz.

   Niestandardowy kod scalania nie będzie miał wpływu na kod, który tworzy obiekty i relacje bezpośrednio, i nie będzie miał wpływu na inne identyfikatory EMD. Aby upewnić się, że dodatkowe zmiany są implementowane niezależnie od sposobu tworzenia elementu, rozważ zamiast tego napisanie `AddRule` elementów `DeleteRule` i . Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Przekierowywanie operacji scalania

Dyrektywa scalania do przodu przekierowuje element docelowy operacji scalania. Zazwyczaj nowy element docelowy jest elementem nadrzędnym osadzania początkowego obiektu docelowego.

Na przykład w DSL, który został utworzony za pomocą szablonu diagramu składników porty są osadzone w składniki. Porty są wyświetlane jako małe kształty na krawędzi kształtu składnika. Użytkownik tworzy porty, przeciągając narzędzie Port do kształtu Składnik. Jednak czasami użytkownik przez pomyłkę przeciąga narzędzie Port na istniejący port, zamiast do składnika, i operacja kończy się niepowodzeniem. Jest to prosty błąd, gdy istnieje kilka istniejących portów. Aby ułatwić użytkownikowi uniknięcie tych problemów, można zezwolić na przeciągnięcie portów na istniejący port, ale przekierowywanie akcji do składnika nadrzędnego. Operacja działa tak, jakby element docelowy był składnikiem.

Dyrektywę scalania do przodu można utworzyć w rozwiązaniu model składników. W przypadku kompilowania i uruchamiania oryginalnego rozwiązania użytkownicy powinni  zobaczyć, że użytkownicy mogą przeciągać dowolną liczbę elementów port wejściowy lub **port** wyjściowy z przybornika **do** **elementu Component.** Nie mogą jednak przeciągać portu do istniejącego portu. Wskaźnik Niedostępny informuje o tym, że to przeniesienie nie jest włączone. Można jednak utworzyć dyrektywę scalania do przodu, tak aby port, który  został niezamierzonie porzucony na istniejącym porcie wejściowym, był przesyłany dalej do **elementu Component.**

### <a name="to-create-a-forward-merge-directive"></a>Aby utworzyć dyrektywę scalania do przodu

1. Utwórz rozwiązanie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] przy użyciu szablonu Model składników.

2. Wyświetl Eksplorator **DSL,** otwierając dslDefinition.dsl.

3. W **Eksploratorze DSL rozwiń** **węzło klasy domen**.

4. Abstrakcyjna **klasa domeny ComponentPort** jest klasą bazową zarówno **klasy InPort,** jak **i OutPort.** Kliknij prawym przyciskiem myszy **pozycję ComponentPort,** a następnie kliknij polecenie Add New Element Merge Directive (Dodaj **nową dyrektywę scalania elementów).**

    W **węźle Dyrektywy scalania** elementów pojawi się nowy węzeł dyrektywy **scalania** elementów.

5. Wybierz węzeł **Dyrektywa scalania elementów** i otwórz **okno Szczegóły DSL.**

6. Na liście Klasy indeksowania wybierz pozycję **ComponentPort**.

7. Wybierz **pozycję Scal do przodu do innej klasy domeny.**

8. Na liście wyboru ścieżki rozwiń pozycję **SkładnikPort,** **rozwiń pozycję SkładnikHasPorty,** a następnie wybierz pozycję **Składnik**.

    Nowa ścieżka powinna wyglądać następująco:

    **ComponentHasPorts.Component/!, składnik**

9. Zapisz rozwiązanie, a następnie przekształć szablony, klikając przycisk znajdujący się po prawej stronie na pasku **Eksplorator rozwiązań** narzędzi.

10. Skompiluj i uruchom rozwiązanie. Zostanie wyświetlone nowe wystąpienie Visual Studio.

11. W **Eksplorator rozwiązań** otwórz program Sample.mydsl. Zostanie wyświetlony diagram **i przybornik ComponentLanguage.**

12. Przeciągnij port **wejściowy z** **przybornika** do innego **portu wejściowego.** Następnie przeciągnij element **OutputPort do** **portu InputPort,** a następnie do innego **portu OutputPort.**

     Wskaźnik Niedostępny nie powinien być wyświetlony i powinno być możliwe upuszczenie nowego **portu wejściowego** na istniejącym porcie. Wybierz nowy port **wejściowy i** przeciągnij go do innego punktu w **składniku**.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md)
- [Przykładowy DSL diagramów obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
