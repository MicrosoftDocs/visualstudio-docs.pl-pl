---
title: Zdefiniuj profil do rozszerania UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bdb6620f8d73bf7fae7b7dbb1b92af38e71345b6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295675"
---
# <a name="define-a-profile-to-extend-uml"></a>Definiowanie profilu w celu rozszerzenia kodu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować *profil UML* , aby dostosować standardowe elementy modelu do określonych celów. Profil definiuje jeden lub więcej *stereotypów UML*. Stereotyp może służyć do oznaczania typu jako reprezentującego określonego rodzaju obiektu. Stereotyp może również zwiększyć listę właściwości elementu.

 Kilka profilów jest instalowanych z obsługiwanymi wersjami programu Visual Studio. Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Aby uzyskać więcej informacji o tych profilach i sposobach stosowania stereotypów, zobacz [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 Możesz zdefiniować własne profile, aby dostosować i zwiększyć funkcjonalność UML do własnego obszaru lub architektury biznesowej. Na przykład:

- Jeśli często definiujesz witryny sieci Web, możesz zdefiniować własny profil, który udostępnia «"Web»" stereotyp, który można zastosować do klas na diagramach klas. Następnie można użyć diagramów klas do zaplanowania witryny sieci Web. Każda Klasa «Strona sieci Web» będzie miała dodatkowe właściwości dla zawartości strony, stylu i tak dalej.

- W przypadku opracowywania oprogramowania bankowego można zdefiniować profil, który udostępnia «"AccountName". Następnie można użyć diagramów klas, aby zdefiniować różne typy kont i pokazać relacje między nimi.

  Własne profile można dystrybuować do zespołu. Każdy członek zespołu może zainstalować swój profil. Dzięki temu można edytować i tworzyć modele, które używają jej stereotypów.

> [!NOTE]
> Jeśli zastosujesz Stereotypy profilu w edytowanym modelu, a następnie udostępnisz go innym osobom, należy zainstalować ten sam profil na swoich komputerach. W przeciwnym razie nie będzie można zobaczyć stereotypów, które zostały użyte.

 Profil jest często częścią większego [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenia. Można na przykład zdefiniować polecenie, które tłumaczy niektóre części modelu na kod. Można zdefiniować profil, który użytkownicy muszą stosować do pakietów, które chcą przetłumaczyć. Nowe polecenie można dystrybuować wraz z profilem w jednym [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzeniu.

 Można również zdefiniować zlokalizowane warianty profilu. Użytkownicy ładujący Twoje rozszerzenie widzą wariant, który jest odpowiedni dla własnej kultury.

## <a name="DefineProfile"></a>Jak zdefiniować profil

#### <a name="to-define-a-uml-profile"></a>Aby zdefiniować profil UML

1. Utwórz nowy plik XML z rozszerzeniem nazwy pliku `.profile`.

2. Dodaj definicje stereotypu zgodnie z wytycznymi opisanymi w [strukturze profilu](#Schema).

3. Dodaj profil do rozszerzenia programu Visual Studio (plik`.vsix`). Można utworzyć nowe rozszerzenie dla profilu lub dodać profil do istniejącego rozszerzenia.

     Zobacz następną sekcję, [jak dodać profil do rozszerzenia programu Visual Studio](#AddProfile).

4. Zainstaluj rozszerzenie na komputerze.

    1. Kliknij dwukrotnie plik rozszerzenia, który ma rozszerzenie nazwy pliku `.vsix`.

    2. Uruchom ponownie program Visual Studio.

5. Upewnij się, że profil został zainstalowany.

    1. Wybierz model w Eksploratorze UML.

    2. W okno Właściwości kliknij właściwość **Profile** . Twój profil zostanie wyświetlony w menu. Ustaw znacznik wyboru obok profilu.

    3. Wybierz element, dla którego profil definiuje stereotypy. W okno Właściwości kliknij właściwość **stereotypy** . Twoje Stereotypy pojawią się na liście. Ustaw znacznik wyboru dla jednego z stereotypów.

    4. Jeśli Twój profil definiuje dodatkowe właściwości dla tego stereotypu, rozwiń Właściwość Stereotype, aby je zobaczyć.

6. Wyślij plik rozszerzenia do innych użytkowników programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby zainstalować je na swoich komputerach.

## <a name="AddProfile"></a>Jak dodać profil do rozszerzenia programu Visual Studio
 Aby zainstalować profil i umożliwić wysyłanie go do innych użytkowników, należy dodać profil do rozszerzenia programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń programu Visual Studio](https://go.microsoft.com/fwlink/?LinkId=160780).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Aby zdefiniować profil w nowym rozszerzeniu programu Visual Studio

1. Utwórz projekt rozszerzenia programu Visual Studio.

   > [!NOTE]
   > Aby można było użyć tej procedury, należy zainstalować [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

   1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

   2. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowane szablony**rozwiń węzeł **Wizualizacja C#** , kliknij pozycję **rozszerzalność**, a następnie kliknij pozycję **Projekt VSIX**. Ustaw nazwę projektu i kliknij przycisk **OK**.

2. Dodaj swój profil do projektu.

   - W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący element**. W oknie dialogowym Znajdź plik profilu.

3. Ustaw właściwość **Kopiuj do pliku wyjściowego** .

   1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik profilu, a następnie kliknij polecenie **Właściwości**.

   2. W okno Właściwości ustaw wartość właściwości **Kopiuj do katalogu wyjściowego** na **zawsze Kopiuj**.

4. W Eksplorator rozwiązań otwórz `source.extension.vsixmanifest`.

    Plik zostanie otwarty w edytorze manifestu rozszerzenia.

5. Na stronie **zasoby** Dodaj wiersz opisujący profil:

   - Kliknij przycisk **Nowy**. Ustaw pola w oknie dialogowym **Dodaj nowe zasoby** w następujący sposób.

   - Ustaw **Typ** na `Microsoft.VisualStudio.UmlProfile`

        Nie jest to jedna z opcji listy rozwijanej. Wprowadź tę nazwę na klawiaturze.

   - Kliknij pozycję **plik w systemie plików** i wybierz nazwę pliku profilu, na przykład `MyProfile.profile`

6. Skompiluj projekt.

7. **Aby debugować profil**, naciśnij klawisz F5.

    Zostanie otwarte doświadczalne wystąpienie programu Visual Studio. W tym przypadku Otwórz projekt modelowania. W Eksploratorze UML wybierz element główny modelu i w okno Właściwości wybierz swój profil. Następnie wybierz elementy wewnątrz modelu i ustaw stereotypy zdefiniowane dla nich.

8. **Aby wyodrębnić VSIX dla wdrożenia**

   1. W Eksploratorze Windows otwórz folder **.\bin\debug** lub **.\bin\Release** , aby znaleźć plik **. vsix** . To jest plik rozszerzenia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Można go zainstalować na komputerze i wysłać do innych użytkowników programu Visual Studio.

   2. Aby zainstalować rozszerzenie:

       1. Kliknij dwukrotnie plik `.vsix`. Zostanie uruchomiony Instalator rozszerzenia programu Visual Studio.

       2. Uruchom ponownie wszystkie wystąpienia programu Visual Studio, które są uruchomione.

   Poniższej alternatywnej procedury można użyć w przypadku małych rozszerzeń, jeśli nie zainstalowano [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Aby zdefiniować rozszerzenie profilu bez użycia zestawu Visual Studio SDK

1. Utwórz katalog systemu Windows, który zawiera następujące trzy pliki:

    - *YourProfile* `.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml` — wpisz tę nazwę, jak pokazano tutaj, z nawiasami kwadratowymi

2. Edytuj `[Content_Types].xml`, aby zawierać poniższy tekst. Należy zauważyć, że zawiera wpis dla każdego rozszerzenia nazwy pliku.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Skopiuj istniejący `extension.vsixmanifest` i edytuj go za pomocą edytora XML. Zmień identyfikator, nazwę i węzły zawartości.

    - Przykład `extension.vsixmanifest` można znaleźć w tym katalogu:

         *dysk* **: \Program Files\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - Węzeł zawartości powinien wyglądać następująco:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Kompresuj trzy pliki do pliku spakowanego.

     W Eksploratorze Windows zaznacz trzy pliki, kliknij prawym przyciskiem myszy, wskaż polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)** .

5. Zmień nazwę pliku spakowanego i zmień jego rozszerzenie nazwy pliku z `.zip` na `.vsix`.

6. Aby zainstalować profil na dowolnym komputerze z odpowiednimi wersjami programu Visual Studio, kliknij dwukrotnie plik `.vsix`.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Aby zainstalować profil UML z rozszerzenia programu Visual Studio

1. Kliknij dwukrotnie plik `.vsix` w Eksploratorze Windows lub Otwórz go w programie Visual Studio.

2. Kliknij przycisk **Instaluj** w wyświetlonym oknie dialogowym.

3. Aby odinstalować lub tymczasowo wyłączyć rozszerzenie, Otwórz **rozszerzenia i aktualizacje** z menu **Narzędzia** .

## <a name="Localized"></a>Jak zdefiniować zlokalizowane profile
 Można zdefiniować różne profile dla różnych kultur lub języków i umieścić je wszystkie w tym samym rozszerzeniu. Gdy użytkownik ładuje Twoje rozszerzenie, zobaczy profil zdefiniowany dla swojej kultury.

 Zawsze musisz podać profil domyślny. Jeśli nie zdefiniowano profilu dla kultury użytkownika, zobaczysz domyślny profil.

#### <a name="to-define-a-localized-profile"></a>Aby zdefiniować zlokalizowany profil

1. Utwórz profil zgodnie z opisem w poprzednich sekcjach,[jak zdefiniować profil](#DefineProfile) i [jak dodać profil do rozszerzenia programu Visual Studio](#AddProfile). Jest to domyślny profil, który będzie używany w dowolnej instalacji, dla której nie jest udostępniany profil zlokalizowany.

2. Dodaj nowy katalog w tym samym katalogu, w którym znajduje się domyślny plik profilu.

    > [!NOTE]
    > Jeśli tworzysz rozszerzenie przy użyciu projektu rozszerzenia programu Visual Studio, użyj Eksplorator rozwiązań, aby dodać nowy folder do projektu.

3. Zmień nazwę nowego katalogu na krótki kod ISO dla zlokalizowanej kultury, np. `bg` dla Bułgarii lub `fr` dla języka francuskiego. Należy używać neutralnego kodu kulturowego, zwykle dwóch liter, a nie określonej kultury, takiej jak `fr-CA`. Aby uzyskać więcej informacji na temat kodów kultur, zobacz [Metoda CultureInfo. GetCultures](https://go.microsoft.com/fwlink/?LinkId=160782), która zawiera kompletną listę kodów kultur.

4. Dodaj kopię domyślnego profilu do nowego katalogu. Nie zmieniaj nazwy pliku.

     Przykładowy folder rozszerzenia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], zanim zostanie skompilowany lub skompresowany do pliku `.vsix`, będzie zawierać następujące foldery i pliki:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Nie należy wstawiać do `extension.vsixmanifest` odwołań do zlokalizowanych wersji profilów. Skopiowane pliki profilów muszą mieć taką samą nazwę jak profil w folderze nadrzędnym.

5. Edytuj nową kopię profilu, dokonując translacji do języka docelowego, wszystkie części, które będą widoczne dla użytkownika, takie jak atrybuty `displayName`.

6. Można utworzyć dodatkowe foldery kultury i zlokalizowane profile dla dowolnej liczby kultur.

7. Kompiluj rozszerzenie programu Visual Studio, tworząc projekt rozszerzenia lub kompresując wszystkie pliki, zgodnie z opisem w poprzednich sekcjach.

## <a name="Schema"></a>Struktura profilu
 Plik XSD dla profilów UML można znaleźć w następującym przykładzie: [ustawienie stereotypów i profili XSD](https://go.microsoft.com/fwlink/?LinkID=213811). Aby ułatwić edytowanie plików profilów, Zainstaluj plik `.xsd` w programie:

 **%ProgramFiles%\Microsoft Visual Studio [wersja] \Xml\Schemas**

 Ta sekcja używa C# profilu jako przykładu. Pełną definicję profilu można zobaczyć w:

 *dysk* **: \Program Files\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**

 Pierwsze części tej ścieżki mogą się różnić w instalacji.

 Aby uzyskać więcej informacji na temat profilu platformy .NET, zobacz [standardowe stereotypy dla modeli UML](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>Główne sekcje definicji profilu UML
 Każdy profil zawiera następującą zawartość:

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> Atrybut o nazwie `name` nie może zawierać spacji ani znaków interpunkcyjnych. Atrybut `displayName`, który pojawia się w interfejsie użytkownika, powinien być prawidłowym ciągiem XML.

 Każdy profil zawiera trzy główne sekcje. W odwrotnej kolejności są one następujące:

- `<propertyTypes>` — lista typów, które są używane dla właściwości zdefiniowanych w sekcji stereotypów.

- `<metaclasses>` — lista typów elementów modelu, do których stosuje się stereotypy w tym profilu, takich jak IClass, IInterface, IOperation, IDependency.

- `<stereotypes>` — definicje stereotypu. Każda definicja zawiera nazwy i typy właściwości, które są dodawane do docelowego elementu modelu.

#### <a name="property-types"></a>Typy właściwości
 Sekcja `<propertyTypes>` deklaruje listę typów, które są używane dla właściwości w sekcji `<stereotypes>`. Istnieją dwa rodzaje typów właściwości: zewnętrzne i Wyliczenie.

 Typ zewnętrzny deklaruje w pełni kwalifikowaną nazwę standardowego typu .NET:

```
<externalType name="System.String" />
```

 Typ wyliczenia definiuje zestaw wartości literału:

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>Metaklasy
 Sekcja `<metaclasses>` jest listą typów elementów modelu, do których można zdefiniować stereotypy w tym profilu:

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 Aby zapoznać się z pełną listą elementów modelu i typów relacji, których można użyć jako klas podklas, zobacz [typy elementów modelu](#Elements).

#### <a name="stereotype-definition"></a>Definicja stereotypu
 Sekcja `<stereotypes>` zawiera jedną lub więcej definicji stereotypu:

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 Każdy stereotyp zawiera jeden lub więcej elementów modelu lub typów relacji, do których można zastosować. Możesz podać nazwę typu podstawowego, aby uwzględnić wszystkie jego typy pochodne. Na przykład, jeśli określisz `Microsoft.VisualStudio.Uml.Classes.IType`, stereotyp można zastosować do `IClass`, `IInterface`, `IEnumeration`i kilku innych typów elementów.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 `name` atrybut `metaclassMoniker` jest link do elementu w sekcji `<metaClasses>`.

> [!NOTE]
> Nazwa monikera musi rozpoczynać się od `/yourProfileName/`, gdzie `yourProfileName` jest zdefiniowana w atrybucie `name` profilu ("CSharpProfile" w tym przykładzie). Moniker zostaje zakończony nazwą jednego z wpisów w sekcji podklas.

 Każdy stereotyp może wyświetlić zero lub więcej właściwości, które dodaje do dowolnego elementu modelu, do którego jest stosowana. `<propertyType>` zawiera link do jednego z typów, które są zdefiniowane w sekcji `<propertyTypes>`. Link musi być `<externalTypeMoniker>`, aby odwołać się do `<externalType>,` lub `<enumerationTypeMoniker>`, aby odwołać się do `<enumerationType>`. Ponownie łącze zaczyna się od nazwy profilu.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="Elements"></a>Typy elementów modelu
 Zestaw typów, dla których można zdefiniować stereotypy, znajduje się na liście [typów elementów modelu UML](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>Rozwiązywanie problemów
 Moje stereotypy nie pojawiają się moje modele UML.
Musisz wybrać swój profil w pakiecie lub modelu. Stereotypy będą wyświetlane w elementach wewnątrz pakietu lub modelu. Aby uzyskać więcej informacji, zobacz [Dodawanie stereotypów do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md).

 Następujący błąd pojawia się, gdy otwieram model UML: **VS1707: nie można załadować następujących profilów, ponieważ wystąpił błąd serializacji: Moja profil. profil**
1. Sprawdź, czy podstawowa składnia XML profilu jest poprawna.

2. Upewnij się, że każda nazwa Moniker ma postać/profileName/nodeName. ProfileName jest wartością atrybutu nazwy w węźle profil główny. Nodename jest wartością atrybutu Name klasy meta, ExternalType lub EnumerationType.

3. Upewnij się, że składnia jest opisana tutaj, i jak pokazano na _dysku_ **: \Program Files\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .

4. Odinstaluj błędne rozszerzenie. Na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

   - Jeśli rozszerzenie nie pojawia się, zobacz następny element.

5. Ponownie skompiluj plik VSIX i otwórz go w Eksploratorze Windows, aby go zainstalować ponownie. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   Rozszerzenie nie pojawia się w Menedżerze rozszerzeń, ale podczas próby ponownego zainstalowania zostanie wyświetlony następujący komunikat: **rozszerzenie jest już zainstalowane dla wszystkich odpowiednich produktów.**
   1. Usuń plik rozszerzenia z podfolderu *LocalAppData*\Microsoft\VisualStudio\\[wersja] \Extensions\

   - Aby wyświetlić *LocalAppData*, należy ustawić opcję Pokaż ukryte pliki i foldery na karcie Widok opcji folderów Eksploratora Windows.

   - *LocalAppData* jest zazwyczaj w C:\Users\\*Nazwa użytkownika*\AppData\Local\

6. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Zobacz też
 [Dodaj stereotypy do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md) [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [standardowych stereotypów dla modeli UML](../modeling/standard-stereotypes-for-uml-models.md) [przykład: kolorowe elementy UML według](https://go.microsoft.com/fwlink/?LinkID=213841) [przykładowego stereotypu: Ustawienie stereotypów, XSD profile](https://go.microsoft.com/fwlink/?LinkID=213811)
