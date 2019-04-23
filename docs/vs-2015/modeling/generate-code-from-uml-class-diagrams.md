---
title: Generowanie kodu z diagramów klas UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 020dd35d225d8629a8061d1a74b234b62960c830
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056162"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generowanie kodu na podstawie diagramów klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wygenerować kod Visual C# .NET z diagramów klas UML w programie Visual Studio, należy użyć **Generuj kod** polecenia. Domyślnie, polecenie generuje typ C# dla każdego wybranego typu UML. Można modyfikować i rozszerzać to zachowanie przez modyfikowanie lub kopiowanie szablonów tekstu, generujących kod. W modelu można określić różne zachowania dla typów, które są zawarte w różnych pakietach.  

 **Generuj kod** polecenia przystosowane jest do generowania kodu z wybranych przez użytkownika elementów oraz do generowania pliku dla każdej klasy UML lub innego elementu. Na przykład zrzut ekranu pokazuje dwa pliki C#, które zostały wygenerowane z dwóch klas UML.  

 Alternatywnie, jeśli chcesz wygenerować kod, w którym wygenerowane pliki nie mają relacji 1:1 z elementami UML, można rozważyć napisanie szablonów tekstowych, które są wywoływane **Przekształć wszystkie szablony** polecenia. Aby uzyskać więcej informacji na temat tej metody, zobacz [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).  

 ![Klasy UML, diagram i wygenerowanego C&#35; klasy plików. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 Aby uzyskać więcej informacji dotyczących diagramów klas UML w programie Visual Studio zobacz następujące tematy:  

- [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)  

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)  

  Aby dowiedzieć się, które wersje programu Visual Studio obsługują diagramów klas UML, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="using-the-generate-code-command"></a>Korzystanie z polecenia Generuj Kod  
 W poniższej procedurze opisano domyślne zachowanie **Generuj kod** polecenia:  

#### <a name="to-generate-a-separate-file-for-each-element"></a>Aby wygenerować osobny plik dla każdego elementu  

1. Utwórz model UML zawierający klasy. Można również zastosować stereotypy do elementów modelu.  

    Aby uzyskać więcej informacji, zobacz [domyślne przekształcenia generowania kodu](#default).  

2. Na diagramie klasy lub w **Eksploratora modelu UML**, wybierz elementy, z których chcesz wygenerować kod. Można wybrać jedną z następujących pozycji:  

   - Określony zbiór elementów.  

   - Pakiet lub model, aby wygenerować kod z jego zawartości.  

   - Diagram, aby zaznaczyć wszystkie elementy na diagramie.  

3. Otwórz menu skrótów dla wybranego elementu, a następnie wybierz **Generuj kod**.  

    Po raz pierwszy używasz **Generuj kod** w określonym modelu pojawi się okno dialogowe. To okno dialogowe pozwala edytować parametry generowania kodu modelu.  

    Wybierz **OK** Jeśli nie masz pewności, że chcesz zmienić te parametry.  

    Aby powrócić do tego okna dialogowego później, należy otworzyć **Eksploratora modelu UML**. Otwórz menu skrótów projektu modelowania, a następnie wybierz **zapasowych generowanie kodu**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie polecenia Generuj kod](#custom).  

   Generowane są pliki zawierające kod C#. Domyślnie generowany jest plik dla każdego typu i pliki są generowane w projekcie biblioteki klas języka C#. Można jednak dostosować to zachowanie. Aby uzyskać więcej informacji, zobacz [Dostosowywanie polecenia Generuj kod](#custom).  

   Pewne testy sprawdzania poprawności są stosowane do modelu w celu zapewnienia, że może on być przetłumaczony na C#. Jeśli testy te nie powiodą się, wyświetlany jest komunikat o błędzie i generowanie kodu nie jest wykonywane. Jeśli utworzono polecenie walidacji menu, kod nie będzie generowany dla każdego elementu, dla którego polecenie walidacji nie powiedzie się. Aby uzyskać więcej informacji, zobacz [definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).  

## <a name="default"></a> Domyślne przekształcenia generacji kodu  
 Ta sekcja zawiera podsumowanie wyników, które są produkowane przez **Generuj kod** polecenia, chyba że Dostosowywanie polecenia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie polecenia Generuj kod](#custom).  

- Dla każdego typu wybranego w modelu UML tworzony jest jeden typ C#. Każdy typ jest umieszczany w osobnym pliku kodu w obszarze **GeneratedCode** folderu.  

- Jeśli typ UML jest zawarty w pakiecie, wygenerowany typ C# jest umieszczony wewnątrz przestrzeni nazw i jest on generowany w folderze, który ma taką samą nazwę jak przestrzeń nazw.  

- Właściwość języka C# jest generowany dla każdego `Attribute` klasy UML.  

- Metodę języka C# jest generowany dla każdego `Operation` typu UML.  

- Pole C# jest generowane dla każdego skojarzenia nawigacyjnego, w którym uczestniczy klasa.  

  Dodając stereotyp do każdego typu UML, można kontrolować więcej właściwości wygenerowanego typu C#.  

|**Aby utworzyć ten typ C#**|**Narysuj ten typ UML**|**Zastosuj ten stereotyp**|  
|---------------------------------|----------------------------|-------------------------------|  
|Class|Class|\<Brak > lub<br /><br /> Klasa C#|  
|Interface|Interface|\<Brak > lub<br /><br /> Interfejs C#|  
|Wyliczenie|Wyliczenie|\<Brak > lub<br /><br /> Wyliczenie C#|  
|Delegate|Class|Delegat C#|  
|Struct|Class|Struktura C#|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Aby ustawić stereotyp na typie lub innym elemencie  

1. Otwórz menu skrótów dla elementu w diagramie lub w **Eksploratora modelu UML**, a następnie wybierz **właściwości**.  

2. W **właściwości** okna, wybierz strzałkę listy rozwijanej w **Stereotypy** właściwości, a następnie zaznacz pole wyboru dla stereotypu, który chcesz zastosować.  

   > [!TIP]
   >  Jeśli stereotypy języka C# nie są wyświetlane, włącz profil C# dla modelu lub pakietu, który zawiera stosowne elementy modelu. Wybierz pakiet lub korzeń modelu w **Eksploratora modelu UML**. Następnie w **właściwości** oknie Wybierz **profilu**, a następnie włącz profil C#.  

3. Rozwiń **Stereotypy** właściwość, aby wyświetlić dodatkowe właściwości, które można ustawić.  

   **Opis** właściwości typów, atrybutów, operacji i skojarzeń są zapisywane w `<summary>` komentarzy w wygenerowanym kodzie. Elementy typu komentarz, są połączone z typami, które są zapisywane w `<remarks>` komentarzy.  

## <a name="varying-the-generated-code"></a>Różnicowanie wygenerowanego kodu  
 Wygenerowany kod zmienia się zależne od właściwości każdego typu, atrybutu lub operacji. Na przykład jeśli ustawisz **jest abstrakcyjny** właściwość klasy na wartość true, a następnie `abstract` — słowo kluczowe pojawi się na wygenerowanej klasy. Jeśli ustawisz **liczebność** atrybutu ** 0..\\ , a następnie wygenerowana właściwość będzie miał `IEnumerable<>` typu.  

 Ponadto, każdy stereotyp zapewnia kilka dodatkowych właściwości, które można ustawiać. Te wartości są tłumaczone na odpowiednie słowa kluczowe w kodzie języka C#. Na przykład, jeśli właściwość jest ustawiona `Is Static` klasy to klasa C# będzie `static`.  

 Aby ustawić te dodatkowe właściwości, zaznacz klasę lub inny element na diagramie. W oknie właściwości rozwiń **Stereotypy**, a następnie rozwiń stereotyp C#, takie jak **klasy C#**.  Dla klas te dodatkowe właściwości obejmują:  

- Atrybuty CLR  

- Jest częściowy  

- Jest statyczny  

- Jest niebezpieczny  

- Widoczność pakietu  

  Każdy atrybut i operacja również ma właściwości stereotypu, które można ustawiać. Jeśli nie ma właściwości na nowym atrybucie, uruchom **Generuj kod**.  

## <a name="custom"></a> Dostosowywanie polecenia Generuj kod  
 **Generuj kod** polecenie działa poprzez przekształcenie elementów modelu przy użyciu zestawu szablonów tekstu. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).  

 Szablony są określone w zestawie *powiązania szablonów tekstu*. Powiązanie szablonu tekstu określa, jaki szablon powinien być stosowany, gdzie ma zostać umieszczony wygenerowanych danych wyjściowych, a inne parametry **Generuj kod** polecenia.  

 Przy pierwszym uruchomieniu **Generuj kod** polecenie określonego modelu dołącza domyślny zestaw powiązań szablonu do korzenia modelu. Te powiązania dotyczą wszystkich elementów w modelu.  

 Można jednak nadpisywać i rozszerzać domyślne powiązania, dołączając własne powiązania do pakietów, klas i innych elementów. Powiązanie stosuje się do wszystkich elementów zawartych w elemencie, do którego jest podłączone. Na przykład, chcąc przekształcić wszystkie typy wewnątrz danego pakietu przez różne zestawy szablonów, lub aby dane wyjściowe znalazły się w innym folderze, można dołączyć powiązania szablonów do pakietu.  

 Aby przeprowadzić inspekcję powiązań dołączonych do elementu modelu, wybierz przycisk wielokropka **[...]**  w **powiązania szablonów tekstu** właściwości w oknie dialogowym właściwości.  

 **Generuj kod** polecenie jest stosowane do każdego elementu modelu, który wybrano szablonów. Dla każdego elementu zestaw zastosowanych szablonów jest połączonym zestawem szablonów, które są dołączone do jego kontenerów i zawierają korzeń modelu.  

 Jeśli dwa powiązania szablonów w zestawie mają taką samą nazwę, powiązanie w mniejszym kontenerze zastąpi powiązanie w większym kontenerze. Na przykład korzeń modelu ma powiązanie o nazwie **szablonu klasy**. Aby utworzyć własny szablon zastosowany do zawartości danego pakietu, zdefiniuj własny szablon powiązania o nazwie **szablonu klasy**.  

 Do elementu modelu można zastosować więcej niż jeden szablon. Z każdego elementu modelu można wygenerować więcej niż jeden plik.  

> [!NOTE]
>  Powiązania dołączone do korzenia modelu działają jako ustawienia domyślne dla wszystkich elementów w modelu. Aby wyświetlić te domyślne powiązania, otwórz **Eksploratora modelu UML**. Otwórz menu skrótów projektu modelowania, a następnie wybierz **zapasowych generowanie kodu**. Alternatywnie możesz wybrać korzeń modelu w Eksploratorze modelu UML. W oknie dialogowym właściwości wybierz **[...]**  w **powiązania szablonów tekstu** właściwości. Powiązania nie będą widoczne, dopóki nie używano **Generuj kod** polecenia co najmniej raz. Szablony powiązań nie mogą być dołączone do diagramu.  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Aby dołączyć powiązanie szablony tekstu do pakietu lub innego elementu modelu  

1. W **Eksploratora modelu UML**, otwórz menu skrótów dla elementu modelu, a następnie wybierz **właściwości**. Na ogół powiązania szablonów tekstu są dołączane do pakietu lub do korzenia modelu.  

2. W **właściwości** okna, wybierz przycisk wielokropka (**[...]** ) w **powiązania szablonów tekstu** właściwości.  

    **Powiązania szablonów tekstu** pojawi się okno dialogowe.  

3. Wybierz **Dodaj** Aby utworzyć nowe powiązanie szablonu tekstu.  

    \- lub —  

    Wybierz istniejące powiązanie, aby je edytować.  

    Każde powiązanie szablonu definiuje, jak określony szablon powinien być stosowany do wybranego elementu modelu i innych elementów modelu, które szablon zawiera.  

4. W oknie dialogowym ustaw właściwości powiązania szablonu tekstu.  

   |    **Property**    |                                                                                                                                                                                                                                                                                                                    **Opis**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Nazwa        |                                                                                                                                                                                                                                                  Nazwa dla tego powiązania. Aby zastąpić powiązanie odziedziczone z zawartego pakietu lub modelu, użyj takiej samej nazwy, jaką ma powiązanie, które chcesz zastąpić.                                                                                                                                                                                                                                                  |
   |     Zastąp      |                                                                                                                                                                                                                                                                                                      Jeśli ma wartość true, istniejący kod jest zastępowany.                                                                                                                                                                                                                                                                                                       |
   |    Nazwa obiektu docelowego     | Nazwa pliku, który jest generowany.<br /><br /> Można wstawiać wyrażenia, w tym ciąg takich jak `{Name}` lub `{Owner.Name}`. Na przykład można napisać: `{Owner.Name}_{Name}`. Wyrażenie jest określane na elemencie modelu. Może używać właściwości elementów, lecz nie metod. Aby dowiedzieć się, jakie właściwości mogą być używane, Przyjrzyj się właściwościom typów w **Microsoft.VisualStudio.Uml.\\ ***. \*\*Ważne:* \* `{Name}` lub `{Owner.Name}` mogą być używane tylko w **Nazwa docelowego** właściwości. Aby zmienić nazwę wygenerowanej klasy, musisz zmodyfikować szablon. Aby uzyskać więcej informacji, zobacz [Writing a Text Template](#writing). |
   |    Ścieżka projektu    |                                                                      Określa ścieżkę do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pliki wyjściowe projektu, który będzie zawierać transformacji. Aby utworzyć nowy projekt skorzystaj z typowanych wartości. Wybierz przycisk wielokropka (**[...]** ) aby wybrać istniejący projekt.<br /><br /> Jeśli projekt nie istnieje zostanie utworzony nowy. Będzie to projekt biblioteki klas języka C#.<br /><br /> Aby to zrobić, musisz wpisać nazwę projektu bezpośrednio. Możesz dołączyć makra zmiennej środowiska, takie jak %ProgramFiles% lub %LocalAppData%.                                                                       |
   |  Katalog docelowy  |                                                                                          Folder, w którym generowany jest plik docelowy. Ścieżka jest względna w stosunku do folderu projektu.<br /><br /> Możesz użyć `{PackageStructure}` wyrażenie, aby wstawić ścieżkę, która odnosi się do nazw zawierających pakietów. Wartość domyślna to `\GeneratedCode\{PackageStructure}`. Można również dołączyć zmienne środowiskowe, takie jak %TEMP% lub %HomePath%. **Ważne:** `{PackageStructure}` mogą być używane tylko w **katalog docelowy** właściwości.                                                                                          |
   | Ścieżka pliku szablonu |                                                                                                                                                           Szablon, który będzie wykonywał przekształcenia.<br /><br /> Można użyć dostarczonych szablonów lub stworzyć własne. Dostarczone szablony można znaleźć w następującej lokalizacji:<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. Można dołączyć dowolną liczbę powiązań do elementu.  

## <a name="writing"></a> Pisanie szablonu tekstowego  
 Można napisać własne szablony tekstu. Szablony tekstu mogą generować kod programu lub dowolnego innego rodzaju plik tekstowy.  

 Firma Microsoft zaleca rozpoczynanie pracy od modyfikowania kopii szablonów standardowych. Szablony można skopiować z następujących lokalizacji:  

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 Informacje na temat szablonów tekstu można znaleźć w następujących tematach.  

- Szablon tekstu jest prototypem wynikowego pliku i zawiera tekst wynikowy i kod programu, który odczytuje model. Aby uzyskać więcej informacji, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).  

- Do nawigacji modelu UML w kodzie programu, należy użyć interfejsu API UML. Aby uzyskać więcej informacji, zobacz [nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md) i [wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  

  Aby użyć szablonów z **Generuj kod** polecenia, trzeba dołączyć dyrektywę modelowania. Na przykład:  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  `ElementType` Atrybut definiuje typ elementu UML, do którego odnosi się ten szablon.  

  W szablonie `this` należy do tymczasowej klasy, która ma następujące właściwości:  

- `Element` = UML <xref:Microsoft.VisualStudio.Uml.Classes.IElement> , do którego zastosowano szablon.  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Aby uzyskać więcej informacji, zobacz [modeli UML, integracja z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).  

- `ProfileName` = "C#Profile"  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Jest to magazyn Visualization and Modeling SDK, w którym zaimplementowano UML ModelStore. Aby uzyskać UML <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, użyj `this.Element.GetModelStore()`.  

  Następujące punkty mogą okazać się pomocne podczas pisania szablonu tekstu. Te informacje są szczegółowo opisane w [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).  

- Można ustawić rozszerzenie nazwy pliku w wyniku w `Output` dyrektywy. Jeden `Output` dyrektywa jest wymagana w każdym szablonie tekstu.  

- Niektóre zestawy są automatycznie dołączane do szablonu. Zestawy te obejmują na przykład: System.dll i Microsoft.VisualStudio.Uml.Interfaces.dll.  

   Aby użyć innych zestawów w generowanym kodzie programu, należy użyć `Assembly` dyrektywy. Na przykład:  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- Niektóre przestrzenie nazw, takich jak `System` są automatycznie importowane do kodu źródłowego. W innych przestrzeniach nazw, można użyć `Import` dyrektywy w taki sam sposób, który zostanie wykorzystany `using` instrukcji. Na przykład:  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- Użyj `Include` dyrektywy, aby odwoływać się do tekstu z innego pliku.  

- Części szablonu w nawiasach `<# ... #>` są wykonywane przez **Generuj kod** polecenia. Części szablonu poza tymi nawiasami są kopiowane do pliku wynikowego. Ważne jest, aby rozróżniać wygenerowany kod od wygenerowanego tekstu. Wygenerowany tekst może być w dowolnym języku.  

- `<#= Expressions #>` obliczone i przekonwertowane na ciągi.  

## <a name="see-also"></a>Zobacz też  
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)   
 [Generowanie plików na podstawie modelu UML](../modeling/generate-files-from-a-uml-model.md)
