---
title: Dostosowywanie tworzenia i przesuwania elementu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f956f492c3dc690ef2edb67d9a7c75e6c0108820
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433270"
---
# <a name="customizing-element-creation-and-movement"></a>Dostosowywanie tworzenia i przesuwania elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zezwolić elementu można przeciągać innym, z przybornika lub wklejenie lub operacji przenoszenia. Może być przeniesione elementy połączone z elementów docelowych przy użyciu relacji, które określisz.  
  
 Dyrektywa scalania (EMD) określa, co się stanie, gdy jest jednym elementem modelu *scalonych* do innego elementu modelu. Dzieje się tak po:  
  
- Użytkownik przeciąga z przybornika do diagramu lub kształtu.  
  
- Użytkownik tworzy element przy użyciu menu Dodaj w Eksploratorze lub kształtu przedziału.  
  
- Użytkownik przenosi element z jednego tor do innego.  
  
- Użytkownik wkleja elementu.  
  
- Kod program wywołuje dyrektywa scalania.  
  
  Mimo że operacje tworzenia mogą wydawać się różnił się od operacji kopiowania, rzeczywistości działają w taki sam sposób. Gdy element zostanie dodany, na przykład z przybornika, jego prototyp są replikowane. Prototyp są scalane w modelu w taki sam sposób, jak elementy, które zostały skopiowane z inną częścią modelu.  
  
  Odpowiedzialność za EMD jest podjęcie decyzji, jak obiekt lub grupę obiektów powinny zostać scalone do określonej lokalizacji w modelu. W szczególności decyduje, jakie relacje należy można utworzyć wystąpienia połączyć grupę scalony do modelu. Można również dostosować, aby ustawić właściwości i utworzyć dodatkowe obiekty.  
  
  ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd-merge.png "DSL-EMD_Merge")  
  Rola w dyrektywie scalania elementów  
  
  EMD jest generowana automatycznie podczas definiowania relacji osadzania. Po dodaniu nowych wystąpień podrzędnych do elementu nadrzędnego, to ustawienie domyślne EMD tworzy wystąpienie relacji. Na przykład te EMDs domyślne można modyfikować, dodając kod niestandardowy.  
  
  Można również dodać własne EMDs w definicji DSL, aby umożliwić użytkownikom przeciągnij lub Wklej różne kombinacje klasy scalonych i odbierania.  
  
## <a name="defining-an-element-merge-directive"></a>Definiowanie dyrektywa scalania  
 Możesz dodać dyrektywy scalania elementów klasy domeny relacje domeny, kształty, łączników i diagramy. Można dodawać lub je znaleźć w Eksplorator DSL w odbieranie klasy domeny. Odbieranie klasa jest klasą domeny elementu, który jest już w modelu i na którym zostaną scalone nowych lub skopiowany element.  
  
 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd-details.png "DSL-EMD_Details")  
  
 **Klasy indeksowania** jest klasą domeny elementów, które może zostać scalony składowe klasy odbierania. Również zostaną scalone wystąpieniami podklasami klasy indeksowania przy tym EMD, chyba że **dotyczy podklas** na wartość False.  
  
 Istnieją dwa rodzaje dyrektywa scalania:  
  
- A **procesu scalania** dyrektywa określa relacji, według których nowego elementu powinna być połączona w drzewie.  
  
- A **do przodu scalania** dyrektywy przekierowuje nowego elementu do innego elementu odbierania, zwykle elementu nadrzędnego.  
  
  Można dodać niestandardowy kod dyrektywy scalania:  
  
- Ustaw **akceptowanie niestandardowe używa** dodać kod do określenia, czy konkretne wystąpienie elementu indeksowania powinny zostać scalone do elementu docelowego. Gdy użytkownik przeciągnie z przybornika, "nieprawidłowy" wskaźnik pokazuje, jeśli kod nie zezwalają na scalania.  
  
   Na przykład można zezwolić scalania, tylko wtedy, gdy element odbieranie znajduje się w określonym stanie.  
  
- Ustaw **używa niestandardowych scalania** dodać Podaj własny kod w celu zdefiniowania zmiany wprowadzone do modelu, gdy przeprowadzane jest scalenie.  
  
   Na przykład można ustawić właściwości w elemencie scalony przy użyciu danych z nowej lokalizacji w modelu.  
  
> [!NOTE]
> Jeśli piszesz kod niestandardowy scalania, dotyczy tylko scaleń, które są wykonywane przy użyciu tego EMD. Czy istnieją inne EMDs, które łączą się ten sam typ obiektu, w przypadku innych kodu niestandardowego, który tworzy te obiekty bez użycia EMD następnie one pozostaną nienaruszone przez kod niestandardowy scalania.  
>   
> Jeśli chcesz upewnić się, że nowy element lub nową relację zawsze jest przetwarzany przez kod niestandardowy, należy wziąć pod uwagę definiowanie `AddRule` relacji osadzania i `DeleteRule` dla klasy domeny elementu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Przykład: Definiowanie EMD bez konieczności pisania kodu niestandardowego  
 Poniższy przykład pozwala użytkownikom na tworzenie elementu i łącznik w tym samym czasie, przeciągając je z przybornika do istniejącego kształtu. W przykładzie dodano EMD do definicji DSL. Przed tą modyfikacją użytkowników można przeciągnąć narzędzia na diagram, ale nie do kształtów.  
  
 Użytkownicy mogą również wkleić elementy do innych elementów.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Aby umożliwić użytkownikom tworzenie elementu i łącznika, w tym samym czasie  
  
1. Tworzenie nowego języka DSL za pomocą **minimalny języka** szablonu rozwiązania.  
  
    Po uruchomieniu tego języka DSL, umożliwia tworzenie kształtów i łączników między kształtami. Nie można przeciągnąć nową **ExampleElement** kształt z przybornika do istniejącego kształtu.  
  
2. Aby umożliwić użytkownikom scalania elementów na `ExampleElement` kształtów, Utwórz nowe EMD w `ExampleElement` klasą domeny:  
  
   1. W **Eksplorator DSL**, rozwiń węzeł **klasami domeny**. Kliknij prawym przyciskiem myszy `ExampleElement` a następnie kliknij przycisk **Dodaj nowe dyrektywa scalania elementów**.  
  
   2. Upewnij się, że **szczegóły języka DSL** okno jest otwarte, tak aby widoczne szczegółowe informacje o nowych EMD. (Menu: **Wyświetl**, **innych Windows**, **szczegóły języka DSL**.)  
  
3. Ustaw **klasa indeksowania** w oknie Szczegóły języka DSL w celu zdefiniowania, jakie klasy elementy mogą zostać scalone na `ExampleElement` obiektów.  
  
    W tym przykładzie wybierz `ExampleElements`, dzięki czemu użytkownik można przeciągnąć nowych elementów na istniejące elementy.  
  
    Należy zauważyć, że klasa indeksowanie staje się nazwa EMD w Eksplorator DSL.  
  
4. W obszarze **Przetwórz scalanie przez utworzenie łącza**, Dodaj dwie ścieżki:  
  
   1. Jedna ścieżka łączy nowego elementu nadrzędnego modelu. Wyrażenie ścieżki, które należy wprowadzić powoduje przejście z istniejącego elementu się za pośrednictwem relacji osadzania do nadrzędnego modelu. Na koniec określa rolę w nowe łącze, do którego zostanie przypisany nowy element. Ścieżka jest w następujący sposób:  
  
       `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
   2. Innej ścieżki łączy nowy element do istniejącego elementu. To wyrażenie ścieżki Określa relacja odwołania i roli, do którego zostanie przypisany nowy element. Ta ścieżka jest następująca:  
  
       `ExampleElementReferencesTargets.Sources`  
  
      Narzędzie nawigacji ścieżki służy do tworzenia każdej ścieżki:  
  
   3. W obszarze **Przetwórz scalanie przez utworzenie linków w ścieżkach**, kliknij przycisk  **\<Dodaj ścieżkę >**.  
  
   4. Kliknij strzałkę listy rozwijanej z prawej strony elementu listy. Zostanie wyświetlony w widoku drzewa.  
  
   5. Rozwiń węzeł w drzewie, aby określić ścieżkę.  
  
5. Przetestuj język DSL:  
  
   1. Naciśnij klawisz F5, aby ponownie skompilować i uruchomić rozwiązanie.  
  
        Ponowne tworzenie będzie trwać dłużej niż zwykle, ponieważ wygenerowany kod będzie można zaktualizować z poziomu szablonów tekstu są zgodne z nową definicję DSL.  
  
   2. Gdy doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] został uruchomiony, otwórz plik modelu DSL. Utwórz niektóre elementy w przykładzie.  
  
   3. Przeciągnij z **Element przykład** narzędzie do istniejącego kształtu.  
  
        Pojawi się nowy kształt i jest połączony do istniejącego kształtu, za pomocą łącznika.  
  
   4. Kopiuj istniejącego kształtu. Wybierz inny kształt i Wklej.  
  
        Zostanie utworzona kopia krawędzi pierwszego kształtu.  Jego nazwa została zmieniona i jest połączony do drugiego kształtu, za pomocą łącznika.  
  
   Zwróć uwagę następujące kwestie z tej procedury:  
  
- Tworząc Scal dyrektyw, można zezwolić dowolnego rodzaju elementu, aby akceptować inne. EMD jest tworzony w odbieranie klasy domeny, a klasa zaakceptowane domeny jest określony w **Index, klasa** pola.  
  
- Definiując ścieżek, można określić łącza, które powinny być używany do łączenia nowy element do istniejącego modelu.  
  
     Łączy, które określisz powinien zawierać jedna relacja osadzania.  
  
- EMD dotyczy zarówno tworzenie z przybornika, a także operacji wklejania.  
  
     Jeśli piszesz kod niestandardowy, który tworzy nowe elementy, możesz jawnie wywołać EMD przy użyciu `ElementOperations.Merge` metody. Dzięki temu kod łączy nowych elementów do modelu w taki sam sposób jak inne operacje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Przykład: Dodawanie kodu EMD akceptowanie niestandardowe  
 Dodając kod niestandardowy do EMD, można zdefiniować bardziej złożone zachowanie scalania. Ten prosty przykład uniemożliwia użytkownikowi dodanie więcej niż określoną liczbę elementów do diagramu. Przykład modyfikuje domyślne EMD, który towarzyszy relacji osadzania.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Aby napisać kod akceptowanie niestandardowe ograniczenia, co użytkownik może dodać  
  
1. Tworzenie języka DSL za pomocą **minimalny języka** szablonu rozwiązania. Otwórz z diagramem definicji DSL.  
  
2. W Eksploratorze DSL rozwiń **klasami domeny**, `ExampleModel`, **dyrektyw scalania**. Wybierz dyrektywa scalania, który nosi nazwę `ExampleElement`.  
  
     Ta EMD Określa, jak użytkownik może utworzyć nowego `ExampleElement` obiekty w modelu, na przykład przeciągając je z przybornika.  
  
3. W **szczegóły języka DSL** wybierz **akceptowanie niestandardowe używa**.  
  
4. Ponownie skompiluj rozwiązanie. To będzie trwać dłużej niż zwykle, ponieważ wygenerowany kod zostanie zaktualizowany z modelu.  
  
     Błąd kompilacji będą zgłaszane, podobnie do: "Company.ElementMergeSample.ExampleElement nie zawiera definicji CanMergeExampleElement..."  
  
     Musisz zaimplementować metodę `CanMergeExampleElement`.  
  
5. Utwórz nowy plik kodu w **Dsl** projektu. Zastąp jego zawartość następującym kodem oraz zmienianie przestrzeni nazw do przestrzeni nazw projektu.  
  
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
  
     Ten prosty przykład ogranicza liczbę elementów, które może zostać scalony z nadrzędnego modelu. Warunki bardziej interesujące metody można sprawdzić właściwości i łącza obiektu odbierania. Można to też sprawdzić właściwości scalania elementów, które są przenoszone w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Aby uzyskać więcej informacji na temat `ElementGroupPrototypes`, zobacz [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md). Aby uzyskać więcej informacji na temat pisania kodu, który odczytuje model, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6. Przetestuj język DSL:  
  
    1. Naciśnij klawisz F5, aby ponownie skompiluj rozwiązanie. Gdy wystąpienie eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie otwarty, otwórz wystąpienie DSL.  
  
    2. Tworzenie nowych elementów na kilka sposobów:  
  
        1. Przeciągnij z **Element przykład** narzędzia na diagram.  
  
        2. W **Eksploratora modelu przykład**, kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij przycisk **Dodaj nowy Element przykład**.  
  
        3. Skopiuj i Wklej elementu na diagramie.  
  
    3. Sprawdź, że nie można użyć dowolnej z następujących sposobów, aby dodać więcej niż cztery elementy w modelu. Jest to spowodowane wszystkich używają dyrektywa scalania.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Przykład: Dodawanie kodu niestandardowego scalania do EMD  
 W kodzie scalania niestandardowego można zdefiniować, co się dzieje, gdy użytkownik przeciągnie narzędzia lub wkleja na element. Istnieją dwa sposoby, aby zdefiniować niestandardowy scalania:  
  
1. Ustaw **używa scalania niestandardowego** i podać kod wymagany. Kod zastępuje scalać wygenerowany kod. Użyj tej opcji, jeśli chcesz całkowicie zmienić definicję działanie scalania.  
  
2. Zastąp `MergeRelate` metodę i opcjonalnie `MergeDisconnect` metody. Aby to zrobić, należy ustawić **Generates Double Derived** właściwość klasy domeny. Kod można wywoływać scalać wygenerowany kod w klasie bazowej. Użyj tej opcji, jeśli chcesz wykonać dodatkowe czynności, po przeprowadzeniu scalania.  
  
   Scaleń, które są wykonywane przy użyciu tego EMD wpływ tylko na tych metod. Jeśli mają wpływ na wszystkie sposoby, w których można utworzyć elementu scalonych alternatywą jest definiowanie `AddRule` relacji osadzania i `DeleteRule` dla klasy domeny scalone. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Aby zastąpić MergeRelate  
  
1. Upewnij się, czy zdefiniowano EMD, do którego chcesz dodać kod w definicji DSL. Jeśli chcesz, możesz dodać ścieżki i zdefiniuj akceptowanie niestandardowe kodu zgodnie z opisem w poprzedniej sekcji.  
  
2. Na diagramie DslDefinition wybierz klasę odbieranie scalania. Zazwyczaj jest klasa na końcu źródła relacji osadzania.  
  
     Na przykład w DSL wygenerowany na podstawie rozwiązania minimalny języka, wybierz pozycję `ExampleModel`.  
  
3. W **właściwości** oknie **Generates Double Derived** do **true**.  
  
4. Ponownie skompiluj rozwiązanie.  
  
5. Sprawdź zawartość **Dsl\Generated Files\DomainClasses.cs**. Wyszukaj metody o nazwie `MergeRelate` i sprawdź ich zawartość. Dzięki temu, dzięki czemu można tworzyć własne wersji.  
  
6. Nowy plik kodu pisać klasę częściową dla klasy odbierania i Zastąp `MergeRelate` metody. Pamiętaj, aby wywołać metodę bazową. Na przykład:  
  
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
  
#### <a name="to-write-custom-merge-code"></a>Aby napisać kod niestandardowy scalania  
  
1. W **Dsl\Generated Code\DomainClasses.cs**, zbadaj metody o nazwie `MergeRelate`. Te metody tworzyć łącza między nowego elementu, a istniejący model.  
  
    Ponadto sprawdź metody o nazwie `MergeDisconnect`. Te metody odłączyć element z modelu, gdy ma zostać usunięty.  
  
2. W **Eksplorator DSL**wybierz lub Utwórz dyrektywa scalania, który chcesz dostosować. W **szczegóły języka DSL** oknie **używa scalania niestandardowego**.  
  
    Po ustawieniu tej opcji **procesu scalania** i **do przodu scalania** opcje są ignorowane. Kod jest używany zamiast tego.  
  
3. Ponownie skompiluj rozwiązanie. Potrwa dłużej niż zwykle, ponieważ pliki wygenerowanego kodu zostaną zaktualizowane z modelu.  
  
    Pojawią się komunikaty o błędach. Kliknij dwukrotnie komunikaty o błędach, aby wyświetlić instrukcje w wygenerowanym kodzie. Te instrukcje poprosić Cię o podanie dwie metody, `MergeRelate` *YourDomainClass* i `MergeDisconnect` *YourDomainClass*  
  
4. Pisanie metod w definicji klasy częściowej w osobnym pliku kodu. Przykłady, których należy sprawdzić wcześniej zasugerować potrzebnych składników.  
  
   Kod niestandardowy scalania nie ma wpływu na kod, który tworzy obiekty i relacje bezpośrednio, a nie wpłynie to na inne EMDs. Aby upewnić się, że dodatkowe zmiany są wykonywane niezależnie od tego, w jaki sposób jest tworzony element, należy wziąć pod uwagę pisania `AddRule` i `DeleteRule` zamiast tego. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Przekierowywanie operacji scalania  
 Dyrektywa scalania do przodu przekierowuje obiekt docelowy operacji scalania. Zazwyczaj nowy obiekt docelowy jest nadrzędny osadzania początkowego elementu docelowego.  
  
 Na przykład w DSL, który został utworzony za pomocą szablonu diagramu składników, porty są osadzone w składnikach. Porty są wyświetlane jako małe kształty na krawędzi kształtu składnik. Użytkownik tworzy portów, przeciągając narzędzie portu na kształt składnika. Jednak czasami użytkownik przeciąga przez pomyłkę narzędzie portu do istniejącego portu, zamiast tego składnika, i kończy się niepowodzeniem. Jest to łatwe błędu, gdy istnieje kilka istniejących portów. Aby ułatwić użytkownikowi, aby uniknąć tego uciążliwy, możesz zezwolić portów można przeciągać istniejącego portu, ale masz akcji przekierowywane do składnika nadrzędnego. Operacja działa tak, jakby elementu docelowego zostały składnika.  
  
 Dyrektywa scalania do przodu można tworzyć w rozwiązaniu składnika modelu. Jeśli skompilować i uruchomić oryginalne rozwiązanie, powinien zostać wyświetlony, że użytkownicy będą mogli przeciągać dowolną liczbę **Port danych wejściowych** lub **Port wyjściowy** elementy z **przybornika** do **Składnika** elementu. Nie można jednak przeciągania portu do istniejącego portu. Niedostępne wskaźnika alertem to przeniesienie nie jest włączona. Jednak można utworzyć to dyrektywa scalania do przodu, tak, że port jest przypadkowo upuszczony na istniejące **Port danych wejściowych** jest przekazywany do **składnika** elementu.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Aby utworzyć to dyrektywa scalania do przodu  
  
1. Utwórz [!INCLUDE[dsl](../includes/dsl-md.md)] rozwiązania przy użyciu szablonu z modelu składników.  
  
2. Wyświetlanie **Eksplorator DSL** , otwierając DslDefinition.dsl.  
  
3. W **Eksplorator DSL**, rozwiń węzeł **klasami domeny**.  
  
4. **Elementu ComponentPort** klasy abstrakcyjnej domeny jest klasą bazową obu **InPort** i **elementu OutPort**. Kliknij prawym przyciskiem myszy **elementu ComponentPort** a następnie kliknij przycisk **Dodaj nowe dyrektywa scalania elementów**.  
  
     Nowy **dyrektywa scalania elementów** pojawia się pod węzłem **dyrektyw scalania** węzła.  
  
5. Wybierz **dyrektywa scalania elementów** węzła i Otwórz **szczegóły języka DSL** okna.  
  
6. Na liście klasy indeksowania wybierz **elementu ComponentPort**.  
  
7. Wybierz **Przekaż Scalanie do innej klasy domeny**.  
  
8. Na liście wyboru ścieżki rozwiń **elementu ComponentPort**, rozwiń węzeł **elementu ComponentHasPorts**, a następnie wybierz pozycję **składnika**.  
  
     Nowa ścieżka powinien przypominać to:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Zapisz rozwiązanie, a następnie przekształcania szablonów, klikając przycisk po prawej stronie **Eksploratora rozwiązań** paska narzędzi.  
  
10. Skompiluj i uruchom rozwiązanie. Nowe wystąpienie klasy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pojawia się.  
  
11. W **Eksploratora rozwiązań**, otwórz Sample.mydsl. Diagram i **przybornika ComponentLanguage** są wyświetlane.  
  
12. Przeciągnij **Port danych wejściowych** z **przybornika** do innego **Port danych wejściowych.** Następnie przeciągnij **OutputPort** do **InputPort** i następnie do innego **OutputPort**.  
  
     Nie powinien niedostępny wskaźnika i powinno być możliwe pomijać nowy **Port danych wejściowych** istniejącą. Wybierz nową **Port danych wejściowych** i przeciągnij go do innego punktu **składnika**.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md)   
 [Przykładowe diagramy obwodu DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
