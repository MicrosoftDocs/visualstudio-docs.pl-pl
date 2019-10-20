---
title: Generowanie kodu na podstawie diagramów klas UML | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75120b2f09c2eba3254a1b94e78875d8130c5225
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666133"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generowanie kodu na podstawie diagramów klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wygenerować kod C# Visual .NET na podstawie diagramów klas UML w programie Visual Studio, użyj polecenia **Generuj kod** . Domyślnie, polecenie generuje typ C# dla każdego wybranego typu UML. Można modyfikować i rozszerzać to zachowanie przez modyfikowanie lub kopiowanie szablonów tekstu, generujących kod. W modelu można określić różne zachowania dla typów, które są zawarte w różnych pakietach.

 Polecenie **Generuj kod** jest szczególnie odpowiednie do generowania kodu z wybranych elementów przez użytkownika, a także do generowania jednego pliku dla każdej klasy UML lub innego elementu. Na przykład zrzut ekranu pokazuje dwa pliki C#, które zostały wygenerowane z dwóch klas UML.

 Alternatywnie, jeśli chcesz wygenerować kod, w którym wygenerowane pliki nie mają relacji 1:1 z elementami UML, możesz rozważyć zapisanie szablonów tekstowych, które są wywoływane za pomocą polecenia **Przekształć wszystkie szablony** . Aby uzyskać więcej informacji na temat tej metody, zobacz [generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).

 ![Diagram klas UML i wygenerowane&#35; pliki klasy C.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Aby uzyskać więcej informacji na temat diagramów klas UML w programie Visual Studio, zobacz następujące tematy:

- [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)

  Aby sprawdzić, które wersje programu Visual Studio obsługują diagramy klas UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="using-the-generate-code-command"></a>Korzystanie z polecenia Generuj Kod
 Poniższa procedura opisuje domyślne zachowanie polecenia **Generuj kod** :

#### <a name="to-generate-a-separate-file-for-each-element"></a>Aby wygenerować osobny plik dla każdego elementu

1. Utwórz model UML zawierający klasy. Można również zastosować stereotypy do elementów modelu.

    Aby uzyskać więcej informacji, zobacz [domyślne przekształcenia generowania kodu](#default).

2. Na diagramie klasy lub w **Eksploratorze modelu UML**wybierz elementy, z których chcesz wygenerować kod. Można wybrać jedną z następujących pozycji:

   - Określony zbiór elementów.

   - Pakiet lub model, aby wygenerować kod z jego zawartości.

   - Diagram, aby zaznaczyć wszystkie elementy na diagramie.

3. Otwórz menu skrótów dla wybranego elementu, a następnie wybierz polecenie **Generuj kod**.

    Przy pierwszym użyciu **generowania kodu** w określonym modelu wyświetlane jest okno dialogowe. To okno dialogowe pozwala edytować parametry generowania kodu modelu.

    Wybierz **przycisk OK** , chyba że wiesz, że chcesz zmienić te parametry.

    Aby później powrócić do tego okna dialogowego, Otwórz **Eksplorator modelu UML**. Otwórz menu skrótów projektu modelowania, a następnie wybierz polecenie **Skonfiguruj generowanie kodu**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie polecenia Generuj kod](#custom).

   Generowane są pliki zawierające kod C#. Domyślnie generowany jest plik dla każdego typu i pliki są generowane w projekcie biblioteki klas języka C#. Można jednak dostosować to zachowanie. Aby uzyskać więcej informacji, zobacz [Dostosowywanie polecenia Generuj kod](#custom).

   Pewne testy sprawdzania poprawności są stosowane do modelu w celu zapewnienia, że może on być przetłumaczony na C#. Jeśli testy te nie powiodą się, wyświetlany jest komunikat o błędzie i generowanie kodu nie jest wykonywane. Jeśli utworzono polecenie walidacji menu, kod nie będzie generowany dla każdego elementu, dla którego polecenie walidacji nie powiedzie się. Aby uzyskać więcej informacji, zobacz [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="default"></a>Domyślne przekształcenia generowania kodu
 Ta sekcja podsumowuje wyniki, które są generowane przez polecenie **Generuj kod** , chyba że zostanie dostosowane polecenie. Aby uzyskać więcej informacji, zobacz [Dostosowywanie polecenia Generuj kod](#custom).

- Dla każdego typu wybranego w modelu UML tworzony jest jeden typ C#. Każdy typ jest umieszczany w osobnym pliku kodu w folderze **GeneratedCode** .

- Jeśli typ UML jest zawarty w pakiecie, wygenerowany typ C# jest umieszczony wewnątrz przestrzeni nazw i jest on generowany w folderze, który ma taką samą nazwę jak przestrzeń nazw.

- C# Właściwość jest generowana dla każdego `Attribute` klasy UML.

- Dla C# każdego `Operation` typu UML jest generowana Metoda.

- Pole C# jest generowane dla każdego skojarzenia nawigacyjnego, w którym uczestniczy klasa.

  Dodając stereotyp do każdego typu UML, można kontrolować więcej właściwości wygenerowanego typu C#.

|**Aby utworzyć ten C# typ**|**Rysuj ten typ UML**|**Zastosuj ten stereotyp**|
|---------------------------------|----------------------------|-------------------------------|
|Class|Class|> \<none lub<br /><br /> Klasa C#|
|Interface|Interface|> \<none lub<br /><br /> Interfejs C#|
|Wyliczenie|Wyliczenie|> \<none lub<br /><br /> Wyliczenie C#|
|Delegate|Class|Delegat C#|
|Struct|Class|Struktura C#|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Aby ustawić stereotyp na typie lub innym elemencie

1. Otwórz menu skrótów dla elementu na diagramie lub w **Eksploratorze modelu UML**, a następnie wybierz **Właściwości**.

2. W oknie **Właściwości** , wybierz strzałkę listy rozwijanej we właściwości **stereotypy** , a następnie zaznacz pole wyboru dla stereotypu, który chcesz zastosować.

   > [!TIP]
   > Jeśli stereotypy języka C# nie są wyświetlane, włącz profil C# dla modelu lub pakietu, który zawiera stosowne elementy modelu. Wybierz pakiet lub katalog główny modelu w **Eksploratorze modelu UML**. Następnie w oknie **Właściwości** wybierz **profil**, a następnie Włącz C# profil.

3. Rozwiń właściwości **stereotypy** , aby wyświetlić dodatkowe właściwości, które można ustawić.

   Właściwości **Description** typów, atrybutów, operacji i skojarzeń są zapisywane do `<summary>` komentarzy w wygenerowanym kodzie. Elementy komentarzy, które są połączone z typami, są zapisywane w komentarzach `<remarks>`.

## <a name="varying-the-generated-code"></a>Różnicowanie wygenerowanego kodu
 Wygenerowany kod zmienia się zależne od właściwości każdego typu, atrybutu lub operacji. Na przykład, jeśli ustawisz właściwość **jest abstrakcyjna** klasy na true, słowo kluczowe `abstract` będzie wyświetlane w wygenerowanej klasie. Jeśli wartość **liczebności** atrybutu zostanie ustawiona na **0.. \*** , wygenerowana właściwość będzie miała typ `IEnumerable<>`.

 Ponadto, każdy stereotyp zapewnia kilka dodatkowych właściwości, które można ustawiać. Te wartości są tłumaczone na odpowiednie słowa kluczowe w kodzie języka C#. Na przykład jeśli ustawisz właściwość `Is Static` w klasie, C# klasa zostanie `static`.

 Aby ustawić te dodatkowe właściwości, zaznacz klasę lub inny element na diagramie. W okno właściwości rozwiń pozycję **stereotypy**, a następnie rozwiń węzeł C# stereotyp, taki jak  **C# Klasa**.  Dla klas te dodatkowe właściwości obejmują:

- Atrybuty CLR

- Jest częściowy

- Jest statyczny

- Jest niebezpieczny

- Widoczność pakietu

  Każdy atrybut i operacja również ma właściwości stereotypu, które można ustawiać. Jeśli właściwości nie są widoczne dla nowego atrybutu, uruchom polecenie **Generuj kod**.

## <a name="custom"></a>Dostosowywanie polecenia Generuj kod
 Polecenie **Generuj kod** działa przez transformowanie elementów modelu przy użyciu zestawu szablonów tekstowych. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

 Szablony są określone w zestawie *powiązań szablonu tekstu*. Powiązanie szablonu tekstu określa, jaki szablon powinien być stosowany, gdzie powinny zostać umieszczone wygenerowane dane wyjściowe oraz inne parametry polecenia **Generuj kod** .

 Gdy po raz pierwszy uruchomisz polecenie **Generuj kod** w określonym modelu, dołączy on domyślny zestaw powiązań szablonu do elementu głównego modelu. Te powiązania dotyczą wszystkich elementów w modelu.

 Można jednak nadpisywać i rozszerzać domyślne powiązania, dołączając własne powiązania do pakietów, klas i innych elementów. Powiązanie stosuje się do wszystkich elementów zawartych w elemencie, do którego jest podłączone. Na przykład, chcąc przekształcić wszystkie typy wewnątrz danego pakietu przez różne zestawy szablonów, lub aby dane wyjściowe znalazły się w innym folderze, można dołączyć powiązania szablonów do pakietu.

 Aby sprawdzić powiązania szablonu dołączone do elementu modelu, wybierz wielokropek **[...]** we właściwości **powiązania szablonu tekstu** w okno właściwości.

 Polecenie **Generuj kod** stosuje szablony do każdego elementu modelu, który został wybrany. Dla każdego elementu zestaw zastosowanych szablonów jest połączonym zestawem szablonów, które są dołączone do jego kontenerów i zawierają korzeń modelu.

 Jeśli dwa powiązania szablonów w zestawie mają taką samą nazwę, powiązanie w mniejszym kontenerze zastąpi powiązanie w większym kontenerze. Na przykład główny model ma powiązanie z **szablonem klasy**nazw. Aby własny szablon został zastosowany do zawartości określonego pakietu, zdefiniuj własne powiązanie szablonu, które ma **szablon klasy**nazwy.

 Do elementu modelu można zastosować więcej niż jeden szablon. Z każdego elementu modelu można wygenerować więcej niż jeden plik.

> [!NOTE]
> Powiązania dołączone do korzenia modelu działają jako ustawienia domyślne dla wszystkich elementów w modelu. Aby wyświetlić te domyślne powiązania, Otwórz **Eksplorator modelu UML**. Otwórz menu skrótów projektu modelowania, a następnie wybierz pozycję **Skonfiguruj generowanie kodu**. Alternatywnie możesz wybrać katalog główny modelu w Eksploratorze modelu UML. W okno właściwości wybierz **[...]** we właściwości **powiązania szablonu tekstu** . Powiązania nie będą wyświetlane do momentu użycia polecenia **Generuj kod** co najmniej raz. Szablony powiązań nie mogą być dołączone do diagramu.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Aby dołączyć powiązanie szablony tekstu do pakietu lub innego elementu modelu

1. W **Eksploratorze modelu UML**Otwórz menu skrótów dla elementu modelu, a następnie wybierz **Właściwości**. Na ogół powiązania szablonów tekstu są dołączane do pakietu lub do korzenia modelu.

2. W oknie **Właściwości** wybierz przycisk wielokropka ( **[...]** ) we właściwości **powiązania szablonu tekstu** .

    Zostanie wyświetlone okno dialogowe **powiązania szablonu tekstu** .

3. Wybierz pozycję **Dodaj** , aby utworzyć nowe powiązanie szablonu tekstu.

    \- lub-

    Wybierz istniejące powiązanie, aby je edytować.

    Każde powiązanie szablonu definiuje, jak określony szablon powinien być stosowany do wybranego elementu modelu i innych elementów modelu, które szablon zawiera.

4. W oknie dialogowym ustaw właściwości powiązania szablonu tekstu.

   |    **Wartość**    |                                                                                                                                                                                                                                                                                                                    **Opis**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Nazwa        |                                                                                                                                                                                                                                                  Nazwa dla tego powiązania. Aby zastąpić powiązanie odziedziczone z zawartego pakietu lub modelu, użyj takiej samej nazwy, jaką ma powiązanie, które chcesz zastąpić.                                                                                                                                                                                                                                                  |
   |     Zastąp      |                                                                                                                                                                                                                                                                                                      Jeśli ma wartość true, istniejący kod jest zastępowany.                                                                                                                                                                                                                                                                                                       |
   |    Nazwa obiektu docelowego     | Nazwa pliku, który jest generowany.<br /><br /> Wyrażenia można wstawiać do tego ciągu, takiego jak `{Name}` lub `{Owner.Name}`. Można na przykład napisać: `{Owner.Name}_{Name}`. Wyrażenie jest określane na elemencie modelu. Może używać właściwości elementów, lecz nie metod. Aby znaleźć właściwości, których można użyć, zapoznaj się z właściwościami typów w **Microsoft. VisualStudio. UML. \*** . \* \*Important: \* \* `{Name}` lub `{Owner.Name}` można używać tylko we właściwości **nazwy docelowej** . Aby zmienić nazwę wygenerowanej klasy, musisz zmodyfikować szablon. Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstu](#writing). |
   |    Ścieżka projektu    |                                                                      Określa ścieżkę do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu, który będzie zawierać pliki wyjściowe transformacji. Aby utworzyć nowy projekt skorzystaj z typowanych wartości. Wybierz przycisk wielokropka ( **[...]** ), aby wybrać istniejący projekt.<br /><br /> Jeśli projekt nie istnieje zostanie utworzony nowy. Będzie to projekt biblioteki klas języka C#.<br /><br /> Aby to zrobić, musisz wpisać nazwę projektu bezpośrednio. Możesz dołączyć makra zmiennej środowiska, takie jak %ProgramFiles% lub %LocalAppData%.                                                                       |
   |  Katalog docelowy  |                                                                                          Folder, w którym generowany jest plik docelowy. Ścieżka jest względna w stosunku do folderu projektu.<br /><br /> Możesz użyć wyrażenia `{PackageStructure}`, aby wstawić ścieżkę, która odpowiada nazw pakietów zawierających. Wartość domyślna to `\GeneratedCode\{PackageStructure}`. Można również dołączyć zmienne środowiskowe, takie jak %TEMP% lub %HomePath%. **Ważne:** `{PackageStructure}` może być używany tylko we właściwości **katalogu docelowego** .                                                                                          |
   | Ścieżka pliku szablonu |                                                                                                                                                           Szablon, który będzie wykonywał przekształcenia.<br /><br /> Można użyć dostarczonych szablonów lub stworzyć własne. Dostarczone szablony można znaleźć w następującej lokalizacji:<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. Można dołączyć dowolną liczbę powiązań do elementu.

## <a name="writing"></a>Pisanie szablonu tekstu
 Można napisać własne szablony tekstu. Szablony tekstu mogą generować kod programu lub dowolnego innego rodzaju plik tekstowy.

 Firma Microsoft zaleca rozpoczynanie pracy od modyfikowania kopii szablonów standardowych. Szablony można skopiować z następujących lokalizacji:

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 Informacje na temat szablonów tekstu można znaleźć w następujących tematach.

- Szablon tekstu jest prototypem wynikowego pliku i zawiera tekst wynikowy i kod programu, który odczytuje model. Aby uzyskać więcej informacji, zobacz sekcję [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

- Do nawigacji modelu UML w kodzie programu, należy użyć interfejsu API UML. Aby uzyskać więcej informacji, zobacz [nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md) i [dokumentacji interfejsu API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

  Aby użyć szablonów z poleceniem **Generuj kod** , musisz uwzględnić dyrektywę modelowania. Na przykład:

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  Atrybut `ElementType` definiuje typ elementu UML, do którego odnosi się ten szablon.

  W szablonie `this` należy do tymczasowej klasy, która ma następujące właściwości:

- `Element` = [IELEMENT](/previous-versions/dd516035(v=vs.140)) UML, do którego jest stosowany szablon.

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). Aby uzyskać więcej informacji, zobacz [integrowanie modeli UML z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- `ProfileName` = "C # profile"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Jest to magazyn Visualization and Modeling SDK, w którym zaimplementowano UML ModelStore. Aby uzyskać [IMODELSTORE](/previous-versions/ee789385(v=vs.140))UML, użyj `this.Element.GetModelStore()`.

  Następujące punkty mogą okazać się pomocne podczas pisania szablonu tekstu. Te informacje są szczegółowo opisane w [szablonach generowanie kodu i tekst T4](../modeling/code-generation-and-t4-text-templates.md).

- Można ustawić rozszerzenie nazwy pliku wyniku w dyrektywie `Output`. W każdym szablonie tekstowym jest wymagana jedna dyrektywa `Output`.

- Niektóre zestawy są automatycznie dołączane do szablonu. Zestawy te obejmują na przykład: System.dll i Microsoft.VisualStudio.Uml.Interfaces.dll.

   Aby użyć innych zestawów w kodzie programu do generowania, należy użyć dyrektywy `Assembly`. Na przykład:

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- Niektóre przestrzenie nazw, takie jak `System`, są automatycznie importowane do kodu programu. W przypadku innych przestrzeni nazw można użyć dyrektywy `Import` w taki sam sposób, jak w przypadku zastosowania instrukcji `using`. Na przykład:

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- Użyj dyrektywy `Include`, aby odwołać się do tekstu innego pliku.

- Części szablonu zawarte w nawiasach `<# ... #>` są wykonywane za pomocą polecenia **Generuj kod** . Części szablonu poza tymi nawiasami są kopiowane do pliku wynikowego. Ważne jest, aby rozróżniać wygenerowany kod od wygenerowanego tekstu. Wygenerowany tekst może być w dowolnym języku.

- `<#= Expressions #>` są oceniane i konwertowane na ciągi.

## <a name="see-also"></a>Zobacz też
 [Diagramy klas UML: referencyjne](../modeling/uml-class-diagrams-reference.md) [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md) [GENERUJą pliki z modelu UML](../modeling/generate-files-from-a-uml-model.md)
