---
title: Dostosowywanie tworzenia i przesuwania elementów
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ea58bb790cf7c9aaac554728643f6e164e06418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654052"
---
# <a name="customizing-element-creation-and-movement"></a>Dostosowywanie tworzenia i przesuwania elementów

Można zezwolić na przeciąganie elementu do innego, z przybornika lub operacji wklejania lub przenoszenia. Elementy przeniesione mogą być połączone z elementami docelowymi przy użyciu określonych relacji.

Dyrektywa scalania elementów (EMD) określa, co się dzieje, gdy jeden element modelu zostanie *scalony* z innym elementem modelu. Dzieje się tak w przypadku:

- Użytkownik przeciągnie z przybornika na diagram lub kształt.

- Użytkownik tworzy element przy użyciu menu Dodaj w Eksploratorze lub kształcie przedziału.

- Użytkownik przenosi element z jednego toru do drugiego.

- Użytkownik wklei element.

- Kod programu wywołuje dyrektywę scalenia elementów.

Chociaż operacje tworzenia mogą się różnić od operacji kopiowania, faktycznie działają w taki sam sposób. Po dodaniu elementu, na przykład z przybornika, prototyp jest replikowany. Prototyp jest scalany z modelem w taki sam sposób, jak elementy, które zostały skopiowane z innej części modelu.

Odpowiedzialnością EMD jest podjęcie decyzji o sposobie scalania obiektu lub grupy obiektów w konkretną lokalizację w modelu. W szczególności decyduje o tym, jakie relacje należy utworzyć, aby połączyć scaloną grupę z modelem. Można również dostosować ją do ustawiania właściwości i tworzenia dodatkowych obiektów.

![Scalanie&#95;EMD DSL&#45;](../modeling/media/dsl-emd_merge.png)

EMD jest generowany automatycznie podczas definiowania relacji osadzania. Ta wartość domyślna EMD tworzy wystąpienie relacji, gdy użytkownicy dodają nowe wystąpienia podrzędne do elementu nadrzędnego. Można modyfikować te domyślne EMDs, na przykład dodając kod niestandardowy.

Możesz również dodać własne EMDs w definicji DSL, aby umożliwić użytkownikom przeciąganie lub wklejanie różnych kombinacji scalonych i otrzymywanych klas.

## <a name="defining-an-element-merge-directive"></a>Definiowanie dyrektywy scalania elementów

Można dodać dyrektywy scalania elementów do klas domeny, relacji domeny, kształtów, łączników i diagramów. Można je dodać lub znaleźć w Eksploratorze DSL w klasie odbiorczej domeny. Klasa odbiorczej jest klasą domeny elementu, który znajduje się już w modelu, i na którym zostanie scalony nowy lub skopiowany element.

![Szczegóły&#45;EMD&#95;DSL](../modeling/media/dsl-emd_details.png)

**Klasa indeksowania** jest klasą domeny elementów, które można scalić do elementów członkowskich klasy odbiorczej. Wystąpienia podklas klasy indeksowania również zostaną scalone przez ten EMD, chyba że ustawisz **dla podklasy** wartości false.

Istnieją dwa rodzaje dyrektywy MERGE:

- Dyrektywa **scalania procesów** określa relacje, za pomocą których nowy element powinien być połączony z drzewem.

- Dyrektywa **scalania do przodu** przekierowuje nowy element do innego elementu, który ma element, zazwyczaj elementu nadrzędnego.

Możesz dodać niestandardowy kod do dyrektyw scalania:

- W ustawieniu **Użyj niestandardowej akceptacji** , aby dodać własny kod w celu ustalenia, czy określone wystąpienie elementu indeksowania powinno zostać scalone z elementem docelowym. Gdy użytkownik przeciągnie z przybornika, wskaźnik "nieprawidłowy" pokazuje, czy Twój kod nie zezwala na scalanie.

   Na przykład można zezwolić na scalanie tylko wtedy, gdy element odbiorcze jest w określonym stanie.

- Zestaw **używa opcji scalania niestandardowe** , aby dodać własny kod w celu zdefiniowania zmian wprowadzonych w modelu podczas przeprowadzania scalania.

   Na przykład można ustawić właściwości w scalonym elemencie przy użyciu danych z nowej lokalizacji w modelu.

> [!NOTE]
> W przypadku pisania niestandardowego kodu scalania ma to wpływ tylko na scalenia, które są wykonywane przy użyciu tego EMD. Jeśli istnieją inne EMDs, które scalają ten sam typ obiektu, lub jeśli istnieje inny kod niestandardowy, który tworzy te obiekty bez użycia EMD, nie będzie to miało wpływu na kod niestandardowego scalania.
>
> Jeśli chcesz upewnić się, że nowy element lub Nowa relacja są zawsze przetwarzane przez niestandardowy kod, rozważ zdefiniowanie `AddRule` w relacji osadzania i `DeleteRule`j klasy domeny elementu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Przykład: Definiowanie EMD bez kodu niestandardowego

Poniższy przykład umożliwia użytkownikom tworzenie elementu i łącznika w tym samym czasie przez przeciąganie z przybornika do istniejącego kształtu. Przykład dodaje EMD do definicji DSL. Przed tą modyfikacją użytkownicy mogą przeciągać narzędzia na diagram, ale nie na istniejących kształtach.

Użytkownicy mogą również wklejać elementy do innych elementów.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Aby umożliwić użytkownikom tworzenie elementu i łącznika w tym samym czasie

1. Utwórz nowy DSL przy użyciu szablonu rozwiązania **minimalnego języka** .

    Po uruchomieniu tego języka DSL można tworzyć kształty i łączniki między kształtami. Nie można przeciągnąć nowego kształtu **przykładElement** z przybornika na istniejący kształt.

2. Aby umożliwić użytkownikom scalanie elementów na `ExampleElement` kształtów, Utwórz nowy EMD w klasie `ExampleElement` domeny:

   1. W **Eksploratorze DSL**rozwiń węzeł **klasy domeny**. Kliknij prawym przyciskiem myszy `ExampleElement` a następnie kliknij pozycję **Dodaj nową dyrektywę scalenia elementów**.

   2. Upewnij się, że okno **Szczegóły DSL** jest otwarte, aby wyświetlić szczegóły nowego EMD. (Menu: **Wyświetl**, **inne okna**, **szczegóły języka DSL**)

3. Ustaw **klasę indeksowania** w oknie Szczegóły DSL, aby zdefiniować klasę elementów, które mogą być scalane na `ExampleElement` obiektów.

    Na potrzeby tego przykładu wybierz `ExampleElements`, aby użytkownik mógł przeciągnąć nowe elementy na istniejące elementy.

    Należy zauważyć, że Klasa indeksowania jest nazwą EMD w Eksploratorze DSL.

4. W obszarze **Scal proces przez utworzenie linków**Dodaj dwie ścieżki:

   - Jedna ścieżka łączy nowy element z modelem nadrzędnym. Wyrażenie ścieżki, które należy wprowadzić nawiguje z istniejącego elementu, w górę za pośrednictwem relacji osadzania z modelem nadrzędnym. Na koniec określa ona rolę w nowym linku, do którego zostanie przypisany nowy element. Ścieżka jest następująca:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - Druga ścieżka łączy nowy element z istniejącym elementem. Wyrażenie path określa relację odwołania i rolę, do której zostanie przypisany nowy element. Ta ścieżka jest następująca:

      `ExampleElementReferencesTargets.Sources`

      Możesz użyć narzędzia do nawigacji ścieżki, aby utworzyć każdą ścieżkę:

      1. W obszarze **Scal proces przez utworzenie linków w ścieżkach**kliknij pozycję **\<add ścieżka >** .

      2. Kliknij strzałkę listy rozwijanej z prawej strony elementu listy. Zostanie wyświetlony widok drzewa.

      3. Rozwiń węzły w drzewie, aby utworzyć ścieżkę, którą chcesz określić.

5. Testowanie DSL:

   1. Naciśnij klawisz **F5** , aby skompilować i uruchomić rozwiązanie.

        Ponowne kompilowanie będzie trwać dłużej niż zwykle, ponieważ wygenerowany kod zostanie zaktualizowany z szablonów tekstowych, aby był zgodny z nową definicją DSL.

   2. Po rozpoczęciu eksperymentalnego wystąpienia programu Visual Studio Otwórz plik modelu DSL. Utwórz Przykładowe elementy.

   3. Przeciągnij z **przykładowego narzędzia elementu** na istniejący kształt.

        Zostanie wyświetlony nowy kształt, który jest połączony z istniejącym kształtem za pomocą łącznika.

   4. Skopiuj istniejący kształt. Wybierz inny kształt i wklej.

        Zostanie utworzona kopia pierwszego kształtu.  Ma nową nazwę i jest połączona z drugim kształtem za pomocą łącznika.

Zwróć uwagę na następujące kwestie z tej procedury:

- Tworząc dyrektywy scalania elementów, można zezwolić dowolnej klasie elementu na akceptowanie innych. EMD jest tworzony w klasie odbiorczej domeny, a zaakceptowana Klasa domeny jest określona w polu **klasy indeksu** .

- Definiując ścieżki, można określić, które linki mają być używane do łączenia nowego elementu z istniejącym modelem.

     Określone linki powinny zawierać jedną relację osadzania.

- EMD dotyczy zarówno tworzenia z przybornika, jak i wklejania operacji.

     W przypadku pisania niestandardowego kodu, który tworzy nowe elementy, można jawnie wywołać EMD za pomocą metody `ElementOperations.Merge`. Daje to pewność, że kod łączy nowe elementy w modelu w taki sam sposób jak inne operacje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Przykład: Dodawanie niestandardowego kodu akceptacji do EMD

Dodając kod niestandardowy do EMD, można zdefiniować bardziej złożone zachowanie scalania. Ten prosty przykład uniemożliwia użytkownikowi Dodawanie więcej niż stałej liczby elementów do diagramu. Przykład modyfikuje domyślny EMD, który towarzyszy relacji osadzania.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Aby napisać niestandardowy kod akceptowania, aby ograniczyć możliwości dodawane przez użytkownika

1. Utwórz DSL przy użyciu szablonu rozwiązania **minimalnego języka** . Otwórz diagram definicji DSL.

2. W Eksploratorze DSL rozwiń węzeł **klasy domen**, `ExampleModel`, **dyrektywy scalania elementów**. Wybierz dyrektywę scalania elementów o nazwie `ExampleElement`.

     Ta EMD określa, jak użytkownik może tworzyć nowe obiekty `ExampleElement` w modelu, na przykład przeciągając je z przybornika.

3. W oknie **Szczegóły DSL** wybierz pozycję **Użyj niestandardowej akceptacji**.

4. Ponownie skompiluj rozwiązanie. To potrwa dłużej niż zwykle, ponieważ wygenerowany kod zostanie zaktualizowany z modelu.

     Zostanie zgłoszony błąd kompilacji, podobny do: "Company. ElementMergeSample. example nie zawiera definicji dla CanMergeExampleElement..."

     Należy zaimplementować metodę `CanMergeExampleElement`.

5. Utwórz nowy plik kodu w projekcie **DSL** . Zastąp jego zawartość następującym kodem i Zmień przestrzeń nazw na przestrzeń nazw projektu.

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

    Ten prosty przykład ogranicza liczbę elementów, które mogą być scalone z modelem nadrzędnym. W celu uzyskania bardziej interesujących warunków Metoda może sprawdzić wszystkie właściwości i linki obiektu odbiorczego. Może również sprawdzać właściwości scalanych elementów, które są przeprowadzane w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Aby uzyskać więcej informacji na temat `ElementGroupPrototypes`, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md). Aby uzyskać więcej informacji na temat pisania kodu, który odczytuje model, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

6. Testowanie DSL:

    1. Naciśnij klawisz **F5** , aby skompilować ponownie rozwiązanie. Gdy zostanie otwarte doświadczalne wystąpienie programu Visual Studio, Otwórz wystąpienie elementu DSL.

    2. Utwórz nowe elementy na kilka sposobów:

        - Przeciągnij z **przykładowego narzędzia elementu** na diagram.

        - W **przykładowym Eksploratorze modelu**kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij polecenie **Dodaj nowy przykładowy element**.

        - Skopiuj i Wklej element na diagramie.

    3. Sprawdź, czy nie możesz użyć żadnego z tych metod, aby dodać więcej niż cztery elementy do modelu. Wynika to z tego, że wszystkie używają dyrektywy scalania elementów.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Przykład: Dodawanie niestandardowego kodu scalania do EMD

W niestandardowym kodzie scalania można zdefiniować, co się stanie, gdy użytkownik przeciągnie narzędzie lub wklei je do elementu. Istnieją dwa sposoby definiowania niestandardowego scalania:

1. Zestaw **używa niestandardowego scalania** i podaj wymagany kod. Kod zastępuje wygenerowany kod scalania. Użyj tej opcji, jeśli chcesz całkowicie przedefiniować elementy do scalenia.

2. Zastąp metodę `MergeRelate` i opcjonalnie metodę `MergeDisconnect`. W tym celu należy ustawić właściwość **Generuj podwójną pochodną** klasy domeny. Kod może wywoływać wygenerowany kod scalania w klasie bazowej. Użyj tej opcji, jeśli chcesz wykonać dodatkowe operacje po przeprowadzeniu scalania.

   Te podejścia mają wpływ tylko na scalenia, które są wykonywane przy użyciu tego EMD. Jeśli chcesz mieć wpływ na wszystkie sposoby tworzenia scalonego elementu, alternatywą jest zdefiniowanie `AddRule` w relacji osadzania i `DeleteRule` w klasie Scalonej domeny. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Aby zastąpić MergeRelate

1. W definicji DSL upewnij się, że zdefiniowano EMD, do którego chcesz dodać kod. Jeśli chcesz, możesz dodać ścieżki i zdefiniować niestandardowy kod akceptacji zgodnie z opisem w poprzednich sekcjach.

2. Na diagramie DslDefinition wybierz klasę otrzymującą scalanie. Zwykle jest to Klasa na końcu źródła relacji osadzania.

     Na przykład w przypadku linii DSL wygenerowanej na podstawie minimalnego rozwiązania językowego wybierz opcję `ExampleModel`.

3. W oknie **Właściwości** ustaw opcję **generują podwójne pochodne** na **true**.

4. Ponownie skompiluj rozwiązanie.

5. Sprawdź zawartość **Dsl\Generated Files\DomainClasses.cs**. Wyszukaj metody o nazwie `MergeRelate` i przejrzyj ich zawartość. Pomoże to napisać własne wersje.

6. W nowym pliku kodu Napisz klasę częściową klasy odbiorczej i Zastąp metodę `MergeRelate`. Pamiętaj, aby wywołać metodę bazową. Na przykład:

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

1. W **Dsl\Generated Code\DomainClasses.cs**, sprawdź metody o nazwie `MergeRelate`. Te metody tworzą linki między nowym elementem a istniejącym modelem.

    Sprawdź również metody o nazwie `MergeDisconnect`. Te metody odłączą element od modelu, gdy zostanie on usunięty.

2. W **Eksploratorze DSL**wybierz lub Utwórz dyrektywę scalania elementów, którą chcesz dostosować. W oknie **Szczegóły DSL** ustaw opcję **Użyj scalania niestandardowego**.

    Po ustawieniu tej opcji Opcje **scalania procesów** i scalania do **przodu** są ignorowane. Zamiast tego używany jest kod.

3. Ponownie skompiluj rozwiązanie. Ten stan będzie trwać dłużej niż zwykle, ponieważ pliki wygenerowanego kodu zostaną zaktualizowane z modelu.

    Pojawią się komunikaty o błędach. Kliknij dwukrotnie komunikaty o błędach, aby wyświetlić instrukcje w wygenerowanym kodzie. Te instrukcje umożliwiają dostarczenie dwóch metod, `MergeRelate`*YourDomainClass* i `MergeDisconnect`*YourDomainClass*

4. Zapisz metody w definicji klasy częściowej w osobnym pliku kodu. Przykłady, które zostały sprawdzone wcześniej, powinny sugerować to, czego potrzebujesz.

   Niestandardowy kod scalania nie będzie mieć wpływu na kod, który tworzy obiekty i relacje bezpośrednio, i nie wpłynie na inne EMDs. Aby upewnić się, że dodatkowe zmiany są zaimplementowane niezależnie od sposobu tworzenia elementu, rozważ zapisanie `AddRule` i `DeleteRule`. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Przekierowywanie operacji scalania

Dyrektywa scalania do przodu przekierowuje miejsce docelowe operacji scalania. Zazwyczaj nowy element docelowy to osadzanie elementu nadrzędnego początkowej lokalizacji docelowej.

Na przykład w DSL, który został utworzony przy użyciu szablonu diagramu składników, porty są osadzone w składnikach. Porty są wyświetlane jako małe kształty na krawędzi kształtu składnika. Użytkownik tworzy porty, przeciągając narzędzie port na kształt składnika. Czasami jednak użytkownik błędnie przeciągnie narzędzie portu na istniejący port zamiast składnika, a operacja kończy się niepowodzeniem. Jest to prosty błąd, gdy istnieje kilka istniejących portów. Aby ułatwić użytkownikowi uniknięcie tych uciążliwości, można zezwolić na przeciąganie portów na istniejący port, ale akcja przekierowana do składnika nadrzędnego. Operacja działa tak, jakby element docelowy był składnikiem.

W rozwiązaniu modelu składników można utworzyć dyrektywę scalania do przodu. Jeśli kompilujesz i uruchomisz oryginalne rozwiązanie, zobaczysz, że użytkownicy mogą przeciągać dowolną liczbę elementów **portu wejściowego** lub **wyjściowego** z **przybornika** do elementu **składnika** . Jednak nie mogą przeciągać portu na istniejący port. Wskaźnik niedostępny informuje o tym, że przeniesienie nie jest włączone. Można jednak utworzyć dyrektywę scalania do przodu, aby port, który przypadkowo został usunięty z istniejącego **portu wejściowego** , został przekazany do elementu **składnika** .

### <a name="to-create-a-forward-merge-directive"></a>Aby utworzyć dyrektywę scalania do przodu

1. Utwórz rozwiązanie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] przy użyciu szablonu modelu składnika.

2. Wyświetl **Eksplorator DSL** , otwierając DslDefinition. DSL.

3. W **Eksploratorze DSL**rozwiń węzeł **klasy domeny**.

4. Klasa abstrakcyjna **ComponentPort** jest klasą bazową obu **portów** **.** Kliknij prawym przyciskiem myszy pozycję **ComponentPort** , a następnie kliknij pozycję **Dodaj nową dyrektywę scalenia elementów**.

    Nowy węzeł **dyrektywy scalania elementów** zostanie wyświetlony w węźle **dyrektywy scalania elementów** .

5. Wybierz węzeł **dyrektywy scalenia elementów** i Otwórz okno **Szczegóły DSL** .

6. Na liście Klasa indeksowania wybierz pozycję **ComponentPort**.

7. Wybierz kolejno pozycje **Prześlij dalej Scalanie do innej klasy domeny**.

8. Na liście wybór ścieżki rozwiń węzeł **ComponentPort**, rozwiń węzeł **elementu ComponentHasPorts**, a następnie wybierz pozycję **składnik**.

    Nowa ścieżka powinna wyglądać następująco:

    **Składnik elementu ComponentHasPorts. Component/!**

9. Zapisz rozwiązanie, a następnie Przekształć szablony, klikając przycisk z prawej na pasku narzędzi **Eksplorator rozwiązań** .

10. Kompiluj i uruchamiaj rozwiązanie. Pojawia się nowe wystąpienie programu Visual Studio.

11. W **Eksplorator rozwiązań**Otwórz przykład. mydsl. Zostanie wyświetlony diagram i **Przybornik ComponentLanguage** .

12. Przeciągnij **port wejściowy** z **przybornika** do innego **portu wejściowego.** Następnie przeciągnij **OutputPort** do **InputPort** , a następnie do innego **OutputPort**.

     Nie powinien być wyświetlany wskaźnik niedostępności i powinien być możliwe porzucenie nowego **portu wejściowego** na istniejącym. Wybierz nowy **port wejściowy** i przeciągnij go do innego punktu w **składniku**.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md)
- [Diagramy obwodów — przykład DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)