---
title: Definiowanie profilu w celu rozszerzenia UML | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b256971cd327098e22b243a1c171b0c9e82d32bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433132"
---
# <a name="define-a-profile-to-extend-uml"></a>Definiowanie profilu w celu rozszerzenia kodu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować *profil UML* dostosować standardowe elementy modelu do określonych celów. Profil, który definiuje co najmniej jeden *stereotypów UML*. Stereotyp może służyć do oznaczenia typu, reprezentując obiekt określonego typu. Stereotyp może także rozszerzać listę elementu właściwości.  
  
 Kilka profilów jest instalowanych z obsługiwanych wersji programu Visual Studio. Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Aby uzyskać więcej informacji o tych profilach i sposobie stosowania stereotypów, zobacz [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
 Można zdefiniować własne profile adaptowanie i rozszerzanie UML do własnych obszarów działalności lub architektury. Na przykład:  
  
- Jeśli często definiujesz witryny sieci Web, można zdefiniować własny profil, który zapewnia stereotyp «WebPage», który może być stosowany do klas na diagramach klas. Można następnie użyć diagramów klas, aby zaplanować witrynę sieci Web. Każda klasa «WebPage» miałaby dodatkowe właściwości dla zawartości strony, stylu i tak dalej.  
  
- W przypadku tworzenia oprogramowania dla banków, można zdefiniować profil, który zawiera stereotyp «Konto». Diagramy klas można następnie użyć do definiowania różnych typów kont i pokazanie relacji między nimi.  
  
  Można dystrybuować własne profile do swojego zespołu. Każdy członek zespołu może zainstalować profil. Umożliwia to edytowanie i tworzenie modeli, które używają tych stereotypów.  
  
> [!NOTE]
> Jeśli zastosujesz Stereotypy profili w modelu edytowanym, a następnie udostępnisz model innym osobom, powinni oni zainstalować ten sam profil na swoich komputerach. W przeciwnym razie nie będą mogli zobaczyć stereotypów, które były używane.  
  
 Profil jest często częścią większego [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenia. Na przykład można zdefiniować polecenie, które tłumaczy niektóre części modelu do kodu. Można zdefiniować profil, który użytkownicy muszą stosować się do pakietów, które chcą tłumaczyć. Będziesz dystrybuować swoje nowe polecenie wraz z profilem w jednym [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenia.  
  
 Można również zdefiniować zlokalizowane warianty profilu. Użytkownicy ładowania rozszerzenia Zobacz wariant, który jest odpowiedni do ich własnej kultury.  
  
## <a name="DefineProfile"></a> Jak zdefiniować profil  
  
#### <a name="to-define-a-uml-profile"></a>Aby zdefiniować profil UML  
  
1. Utwórz nowy plik XML z rozszerzeniem nazwy pliku `.profile`.  
  
2. Dodaj definicje stereotypu zgodnie z wytycznymi opisany w [struktury profilu](#Schema).  
  
3. Dodać profil do rozszerzenia programu Visual Studio (`.vsix` pliku). Możesz utworzyć nowe rozszerzenie dla swojego profilu lub dodać profil do istniejącego rozszerzenia.  
  
     Zobacz następną sekcję [sposób dodać profil do rozszerzenia programu Visual Studio](#AddProfile).  
  
4. Na komputerze, należy zainstalować rozszerzenie.  
  
    1. Kliknij dwukrotnie plik rozszerzenia, który ma rozszerzenie nazwy pliku `.vsix`.  
  
    2. Uruchom ponownie program Visual Studio.  
  
5. Sprawdź, czy profil został zainstalowany.  
  
    1. Wybierz model w Eksploratorze UML.  
  
    2. W oknie dialogowym właściwości kliknij **profile** właściwości. Twój profil będzie wyświetlane w menu. Ustaw znacznik wyboru obok profilu.  
  
    3. Wybierz element, dla którego profil definiuje stereotypy. W oknie dialogowym właściwości kliknij **Stereotypy** właściwości. Twoje Stereotypy pojawią się na liście. Ustaw znacznik wyboru przeciwko jednemu ze stereotypów.  
  
    4. Jeśli Twój profil definiuje dodatkowe właściwości tego stereotypu, rozwiń właściwości stereotypu, aby je wyświetlić.  
  
6. Wyślij rozszerzenie pliku dla innych użytkowników [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do zainstalowania na swoich komputerach.  
  
## <a name="AddProfile"></a> Jak dodać profil do rozszerzenia programu Visual Studio  
 Aby zainstalować profil i umożliwić wysyłanie go do innych użytkowników, należy dodać profil do rozszerzenia programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Aby zdefiniować profil w nowym rozszerzeniu Visual Studio  
  
1. Utwórz projekt rozszerzenia Visual Studio.  
  
   > [!NOTE]
   > Musisz mieć zainstalowane [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Aby użyć tej procedury.  
  
   1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
   2. W **nowy projekt** dialogowego **zainstalowane szablony**, rozwiń węzeł **Visual C#**, kliknij przycisk **rozszerzalności**, a następnie kliknij przycisk  **Projekt VSIX**. Ustaw nazwę projektu, a następnie kliknij przycisk **OK**.  
  
2. Dodaj własny profil do projektu.  
  
   - W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący element**. W oknie dialogowym zlokalizuj plik profilu.  
  
3. Ustaw plik profilu **Kopiuj do katalogu wyjściowego** właściwości.  
  
   1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik profilu, a następnie kliknij przycisk **właściwości**.  
  
   2. W oknie właściwości ustaw **Kopiuj do katalogu wyjściowego** właściwości **zawsze Kopiuj**.  
  
4. W Eksploratorze rozwiązań Otwórz `source.extension.vsixmanifest`.  
  
    Plik zostanie otwarty w edytorze manifesty rozszerzenia.  
  
5. Na **zasoby** strony, Dodaj wiersz opisu profilu:  
  
   - Kliknij przycisk **Nowy**. Ustaw pola w **Dodaj nowy zasób** okno dialogowe w następujący sposób.  
  
   - Ustaw **typu** do `Microsoft.VisualStudio.UmlProfile`  
  
        Nie jest jedną z opcji listy rozwijanej. Wprowadź tę nazwę przy użyciu klawiatury.  
  
   - Kliknij przycisk **plików w systemie plików** i nazwa pliku profilu, na przykład wybrać `MyProfile.profile`  
  
6. Skompiluj projekt.  
  
7. **Aby debugować profil**, naciśnij klawisz F5.  
  
    Otwiera doświadczalne wystąpienie programu Visual Studio. W tym wypadku Otwórz projekt modelowania. W Eksploratorze UML wybierz element główny modelu i w oknie dialogowym właściwości, wybierz swój profil. Wybierz elementy wewnątrz modelu i ustawi Stereotypy zdefiniowane dla nich.  
  
8. **Aby wyodrębnić VSIX dla wdrażania**  
  
   1. W Eksploratorze Windows otwórz folder **.\bin\Debug** lub **.\bin\Release** można znaleźć **.vsix** pliku. Jest to [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenie pliku. Może być zainstalowana na danym komputerze i wysyłane do innych użytkowników programu Visual Studio.  
  
   2. Aby zainstalować rozszerzenie:  
  
       1. Kliknij dwukrotnie `.vsix` pliku. Zostanie uruchomiony Instalator rozszerzenia programu Visual Studio.  
  
       2. Ponowne uruchomienie wystąpienia programu Visual Studio, które są uruchomione.  
  
   Poniższa alternatywna procedura może służyć do małych rozszerzeń małych, jeśli nie zainstalowano [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Aby zdefiniować rozszerzenie profilu bez korzystania z programu Visual Studio SDK  
  
1. Utwórz katalog Windows, który zawiera następujące trzy pliki:  
  
    - *YourProfile* `.profile`  
  
    - `extension.vsixmanifest`  
  
    - `[Content_Types].xml` — Wpisz nazwę, jak pokazano tutaj z nawiasami kwadratowymi  
  
2. Edytuj `[Content_Types].xml` zawierać poniższy tekst. Należy zauważyć, że zawiera on wpis dla każdego rozszerzenia nazwy pliku.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
      <Default Extension="profile" ContentType="application/octet-stream" />  
      <Default Extension="vsixmanifest" ContentType="text/xml" />  
    </Types>  
    ```  
  
3. Kopiuje istniejący `extension.vsixmanifest` i edytuje za pomocą edytora XML. Zmienić identyfikator, nazwę oraz zawartość węzłów.  
  
    - Można znaleźć przykład `extension.vsixmanifest` w tym katalogu:  
  
         *dysk* **: \Program Files\Microsoft \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles programu Visual Studio [wersja]**  
  
    - Węzeł zawartości powinien być następujący:  
  
        ```  
        <Content>  
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"  
          >YourProfile.Profile</CustomExtension>  
        </Content>  
        ```  
  
4. Skompresuj trzy pliki do postaci pliku zip.  
  
     W Eksploratorze Windows, wybierz trzy pliki, kliknij prawym przyciskiem myszy, wskaż **Wyślij do**, a następnie kliknij przycisk **skompresowany folder (zip)**.  
  
5. Zmień nazwę pliku zip i zmień jego rozszerzenie nazwy pliku z `.zip` do `.vsix`.  
  
6. Aby zainstalować profil na każdym komputerze z odpowiedniej wersji programu Visual Studio, kliknij dwukrotnie `.vsix` pliku.  
  
#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Aby zainstalować profil UML z rozszerzenia programu Visual Studio  
  
1. Kliknij dwukrotnie `.vsix` plików w Eksploratorze Windows, lub otworzyć go w programie Visual Studio.  
  
2. Kliknij przycisk **zainstalować** w zostanie wyświetlone okno dialogowe.  
  
3. Aby odinstalować lub tymczasowo wyłączyć rozszerzenie, otwórz **rozszerzenia i aktualizacje** z **narzędzia** menu.  
  
## <a name="Localized"></a> Jak zdefiniować zlokalizowane profile  
 Można zdefiniować różne profile dla różnych kultur lub języków i spakować je wszystkie w tym samym rozszerzeniu. Gdy użytkownik wczytuje Twojego rozszerzenia, zobaczy profil, który zostały zdefiniowane dla jego kultury.  
  
 Należy zawsze podać domyślny profil. Jeśli nie zdefiniowano profilu dla kultury użytkownika, zobaczy profil domyślny.  
  
#### <a name="to-define-a-localized-profile"></a>Aby zdefiniować zlokalizowany profil  
  
1. Utwórz profil, zgodnie z opisem w poprzedniej sekcji[sposób definiowania profilu](#DefineProfile) i [sposób dodać profil do rozszerzenia programu Visual Studio](#AddProfile). To jest domyślny profil i będzie używana w żadnej instalacji, dla którego nie są oferowane zlokalizowany profil.  
  
2. Dodaj nowy katalog, w tym samym katalogu co plik profilu domyślnego.  
  
    > [!NOTE]
    > Jeśli tworzysz rozszerzenie za pomocą projektu rozszerzenia Visual Studio, należy używać Eksploratora rozwiązań, aby dodać nowy folder do projektu.  
  
3. Zmień nazwę nowego katalogu na krótki kod ISO dla zlokalizowanej kultury, takie jak `bg` dla języka bułgarskiego lub `fr` francuski. Należy używać kodu kultury neutralnej, zazwyczaj dwóch liter, określonej kultury takiej jak `fr-CA`. Aby uzyskać więcej informacji na temat kodów kultury, zobacz [metoda CultureInfo.GetCultures](http://go.microsoft.com/fwlink/?LinkId=160782), który zawiera pełną listę kodów kultur.  
  
4. Dodaj kopię profilu domyślnego do nowego katalogu. Nie zmieniaj nazwy pliku.  
  
     Przykład [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] folder rozszerzenia, zanim zostanie skompilowany lub skompresowany do `.vsix` plik, będzie zawierać następujące foldery i pliki:  
  
     `extension.vsixmanifest`  
  
     `MyProfile.profile`  
  
     `fr\MyProfile.profile`  
  
     `de\MyProfile.profile`  
  
    > [!NOTE]
    > Nie należy wstawiać do `extension.vsixmanifest` odwołanie do zlokalizowanych wersji profilów. Pliki kopiowanego profilu muszą mieć taką samą nazwę jak profil w folderze nadrzędnym.  
  
5. Edytuj tę nową kopię profilu, co przekłada się język docelowy wszystkich części, które będą widoczne dla użytkownika, takie jak `displayName` atrybutów.  
  
6. Można tworzyć foldery dodatkowe kultury i zlokalizowane programy profilowania dla tylu kultur, jak chcesz.  
  
7. Tworzenie rozszerzenia programu Visual Studio, przez kompilację projektu rozszerzeń lub kompresowanie wszystkich plików zgodnie z opisem w poprzedniej sekcji.  
  
## <a name="Schema"></a> Struktura profilu  
 Plik XSD dla profilów UML można znaleźć w następującym przykładzie: [Ustawienie stereotypów i profili XSD](http://go.microsoft.com/fwlink/?LinkID=213811). Aby edytować pliki profilu, zainstaluj `.xsd` w pliku:  
  
 **%ProgramFiles%\Microsoft visual Studio [wersja] \Xml\Schemas**  
  
 Ta sekcja używa profilu C# jako przykładu. Definicję kompletnego profil można zobaczyć w:  
  
 *dysk* **: \Program Files\Microsoft \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile programu Visual Studio [wersja]**  
  
 Pierwsze części tej ścieżki mogą różnić się w tej instalacji.  
  
 Aby uzyskać więcej informacji na temat profilu .NET, zobacz [standardowe stereotypy dla modeli UML](../modeling/standard-stereotypes-for-uml-models.md).  
  
### <a name="main-sections-of-the-uml-profile-definition"></a>Główne sekcje definicji profilu UML  
 Każdy profil zawiera następujące treści:  
  
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
> Atrybut o nazwie `name` nie może zawierać spacji i znaków przestankowych. Ten atrybut `displayName`, która jest wyświetlana w interfejsie użytkownika powinna być prawidłowym ciągiem XML.  
  
 Każdy profil zawiera trzy główne sekcje. W odwrotnej kolejności są one w następujący sposób:  
  
- `<propertyTypes>` — Lista typów, które są używane dla właściwości zdefiniowanych w sekcji stereotypów.  
  
- `<metaclasses>` — Lista typów elementów modelu, do których stereotypy w tym profilu zastosować, takie jak IClass, IInterface, IOperation, IDependency.  
  
- `<stereotypes>` — definicje stereotypu. Każda definicja obejmuje nazwy i typy właściwości, które są dodawane do elementu modelu docelowego.  
  
#### <a name="property-types"></a>Typy właściwości  
 `<propertyTypes>` Sekcja określa listę typów, które są używane do właściwości w `<stereotypes>` sekcji. Istnieją dwa rodzaje typów właściwości: zewnętrzne i wyliczenie.  
  
 Typ zewnętrzny deklaruje w pełni kwalifikowaną nazwę standardowej platformy .NET typu:  
  
```  
<externalType name="System.String" />  
```  
  
 Typ wyliczany definiuje zestaw wartości literałów:  
  
```  
<enumerationType name="PackageVisibility">  
  <enumerationLiterals>  
    <enumerationLiteral name="internal" displayName="internal"  />  
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />  
  </enumerationLiterals>  
</enumerationType>  
```  
  
#### <a name="metaclasses"></a>Metaklasy  
 `<metaclasses>` Sekcja jest listą typów elementu modelu, do których można zdefiniować stereotypy w tym profilu:  
  
```  
<metaclass   
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />  
<metaclass  
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />  
```  
  
 Aby uzyskać pełną listę typów elementów i relacji modeli, których można użyć jak metaklasy, zobacz [typy elementów modelu](#Elements).  
  
#### <a name="stereotype-definition"></a>Definicja stereotypu  
 `<stereotypes>` Sekcja zawiera jedną lub więcej definicji stereotypu:  
  
```  
<stereotype name="CSharpClass" displayName="C# Class"> ...  
```  
  
 Każdy stereotyp Wyświetla listę przynajmniej jednego modelu elementu lub typów relacji do których mogą być stosowane. Można nadać nazwę typu podstawowego, aby uwzględnić jego typy pochodne. Na przykład, jeśli określisz `Microsoft.VisualStudio.Uml.Classes.IType`, stereotyp można zastosować do `IClass`, `IInterface`, `IEnumeration`oraz kilka innych typów elementów.  
  
```  
<metaclasses>  
  <metaclassMoniker name=  
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />  
</metaclasses>  
```  
  
 `name` Atrybutu `metaclassMoniker` łącze do elementu w `<metaClasses>` sekcji.  
  
> [!NOTE]
> Nazwa monikera musi zaczynać się `/yourProfileName/`, gdzie `yourProfileName` jest zdefiniowany w `name` atrybut profilu ("CSharpProfile" w tym przykładzie). Moniker kończy się nazwą jednego z wpisów w sekcji metadanych.  
  
 Każdy stereotyp może zawierać zero lub więcej właściwości, które dodaje do dowolnego elementu modelu, do którego jest stosowany. `<propertyType>` Zawiera łącze do jednego z typów, które są zdefiniowane w `<propertyTypes>` sekcji. Łącze musi być albo `<externalTypeMoniker>` do odwoływania się do `<externalType>,` lub `<enumerationTypeMoniker>` do odwoływania się do `<enumerationType>`. Ponownie łącze zaczyna się od nazwy profilu.  
  
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
  
## <a name="Elements"></a> Typy elementów modelu  
 Zestaw typów, dla których można zdefiniować Stereotypy znajduje się w [typy elementów modelu UML](../modeling/uml-model-element-types.md).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Moje Stereotypy nie pojawiają się moich modelach UML.  
 Musisz wybrać profil w paczce lub modelu. Stereotypy pojawią się na elementach wewnątrz pakietu lub modelu. Aby uzyskać więcej informacji, zobacz [elementów modelu UML Stereotypy Dodaj](../modeling/add-stereotypes-to-uml-model-elements.md).  
  
 Jest wyświetlany następujący błąd podczas otwierania modelu UML: **VS1707: Nie można załadować następujące profile, ponieważ wystąpił błąd serializacji: MyProfile.profile**  
1. Sprawdź poprawność podstawowego podstawową składnia XML.  
  
2. Upewnij się, że każda nazwa Moniker jest w postaci/ProfileName/nodename. Nazwa_profilu jest wartością atrybutu nazwy w węźle głównym profilu. Nazwa węzła jest wartością atrybutu nazwy Metaklasa, externalType lub enumerationType.  
  
3. Upewnij się, składnia jest zgodnie z opisem w tym miejscu oraz jak pokazano w _dysku_**: \Program Files\Microsoft \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles programu Visual Studio [wersja]\\** .  
  
4. Odinstaluj wadliwe rozszerzenie. Na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.  
  
   - Jeśli rozszerzenie nie jest wyświetlany, zobacz następną sekcję.  
  
5. Rekonstruowanie pliku VSIX, a następnie otwórz go w Eksploratorze Windows, aby zainstalować go ponownie. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   Rozszerzenie nie pojawia się w Menedżerze rozszerzeń, ale podczas próby zainstalowania go ponownie, zostanie wyświetlony następujący komunikat: **Rozszerzenie jest już zainstalowana na wszystkich dających się zastosować produktów.**  
   1. Usuń rozszerzenie pliku z podfolderu *LocalAppData*\Microsoft\VisualStudio\\\Extensions\ [wersja]  
  
   - Aby wyświetlić *LocalAppData*, należy ustawić ukryte pliki i foldery, które znajdują się w zakładce widok Opcje folderów w Eksploratorze Windows.  
  
   - *LocalAppData* znajduje się zwykle w C:\Users\\*userName*\AppData\Local\  
  
6. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie stereotypów do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Standardowe stereotypy dla modeli UML](../modeling/standard-stereotypes-for-uml-models.md)   
 [Przykład: Kolor elementów UML przez stereotyp](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Przykład: Stereotypy ustawienia, profile XSD](http://go.microsoft.com/fwlink/?LinkID=213811)
