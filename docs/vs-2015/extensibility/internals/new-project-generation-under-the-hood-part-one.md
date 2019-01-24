---
title: 'Generowanie nowego projektu: Za kulisami, część jednego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d28305f8ccd1a6b212b520a7501164be2cc0ee
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777633"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generowanie nowego projektu: Kulisami część pierwsza
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nigdy nie myśl o tym, jak utworzyć swój własny typ projektu? Zastanawiasz się, co rzeczywiście się dzieje po utworzeniu nowego projektu? Teraz wykonać podglądu pod maską i zobacz, co naprawdę dzieje.  
  
 Istnieje kilka zadań, które współrzędne programu Visual Studio:  
  
-   Wyświetla drzewo wszystkich typów dostępnych projektów.  
  
-   On Wyświetla listę szablonów aplikacji dla każdego typu projektu i umożliwia wybranie jednej.  
  
-   Zbiera informacje o projekcie dla aplikacji, na przykład nazwę i ścieżkę projektu.  
  
-   Przekazuje te informacje do fabryki projektu.  
  
-   Generuje on elementy projektu i foldery w bieżącym rozwiązaniu.  
  
## <a name="the-new-project-dialog-box"></a>Okno dialogowe Nowy projekt  
 Wszystko zaczyna się po wybraniu typu projektu dla nowego projektu. Zacznijmy od kliknięcie **nowy projekt** na **pliku** menu. **Nowy projekt** pojawi się okno dialogowe, wyglądające podobnie do następującej:  
  
 ![Okno dialogowe Nowy projekt](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Przyjrzyjmy się im bliżej przyjrzeć. **Typów projektów** drzewa Wyświetla listę różnych typów projektów, można utworzyć. Po wybraniu typu projektu, takich jak **Visual C# Windows**, zobaczysz listę szablonów aplikacji, które ułatwią Ci rozpoczęcie pracy. **Zainstalowane szablony programu Visual Studio** instalowanych przez program Visual Studio i są dostępne dla każdego użytkownika komputera. Nowe szablony, które można tworzyć lub zebrać mogą być dodawane do **Moje szablony** i są dostępne tylko dla Ciebie.  
  
 Po wybraniu szablonu, takie jak **aplikacji Windows**, opis typu aplikacji jest wyświetlany w oknie dialogowym; w tym przypadku **projekt służący do tworzenia aplikacji za pomocą interfejsu użytkownika Windows**.  
  
 W dolnej części **nowy projekt** okno dialogowe pojawi się kilka formantów, które zebrać więcej informacji. Formanty, zostanie wyświetlony zależą od typu projektu, ale zazwyczaj obejmują one projektu **nazwa** pole tekstowe **lokalizacji** pole tekstowe i pokrewnych **Przeglądaj** przycisk i **Nazwa rozwiązania** pole tekstowe i pokrewnych **Utwórz katalog rozwiązania** pole wyboru.  
  
## <a name="populating-the-new-project-dialog-box"></a>Wypełnianie okna dialogowego Nowy projekt  
 Gdzie jest **nowy projekt** okno dialogowe uzyskać informacji o jej? Istnieją dwa mechanizmy, w tym miejscu pracy, jeden z nich jest przestarzałe. **Nowy projekt** okno dialogowe łączy i wyświetla informacje uzyskane z obu mechanizmów.  
  
 Starsza metoda (przestarzałe) korzysta z wpisy rejestru systemowego i plików .vsdir. Ten mechanizm jest uruchamiany po otwarciu programu Visual Studio. Metoda nowszej używa plików .vstemplate. Ten mechanizm jest uruchamiany podczas inicjowania programu Visual Studio, na przykład, uruchamiając  
  
```  
devenv /setup  
```  
  
 lub  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Typy projektów  
 Położenie i nazwy **typów projektów** główne węzły, takich jak **Visual C#** i **inne języki**, jest określana przez wpisy rejestru systemowego. Organizowanie węzłów podrzędnych, takich jak **bazy danych** i **urządzeń inteligentnych**, odzwierciedla hierarchię folderów, które zawierają odpowiadające im pliki vstemplate. Przyjrzyjmy się węzły główne najpierw.  
  
#### <a name="project-type-root-nodes"></a>Węzły główne typu projektu  
 Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest zainicjowany, przechodzi przez podkluczy klucza rejestru systemu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs do tworzenia i nazwy węzłów głównych **typówprojektów** drzewa. Te informacje są buforowane w celu późniejszego użycia. Przyjrzyj się TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 klucza. Każdy wpis jest identyfikator GUID pakietu VSPackage. Nazwa podklucza (/ 1) jest ignorowany, ale jego obecność oznacza, że jest **typów projektów** węzła głównego. Węzeł główny z kolei może mieć kilka podkluczy, które kontrolują wygląd w **typów projektów** drzewa. Spójrzmy na niektóre z nich.  
  
##### <a name="default"></a>(Domyślnie)  
 To jest identyfikator zasobu ciągu zlokalizowane nazwy węzła głównego. Zasób ciągu znajduje się w towarzyszącej bibliotece DLL wybranych przez identyfikator GUID pakietu VSPackage.  
  
 W tym przykładzie jest identyfikator GUID pakietu VSPackage  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 i identyfikator zasobu (wartość domyślna) węzła głównego (/ 1) jest #2345  
  
 Jeśli wyszukiwanie identyfikatora GUID w pobliżu klucz pakietów i sprawdzić podklucz SatelliteDll, można znaleźć ścieżkę do zestawu, który zawiera zasób ciągu:  
  
 \<Ścieżka instalacji usługi Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Aby to sprawdzić, otwórz Eksploratora plików, a następnie przeciągnij csprojui.dll do katalogu programu Visual Studio... Tabela ciągów pokazuje, że zasób #2345 ma podpis **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Określa położenie węzeł główny na **typów projektów** drzewa.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Im mniejsza liczba priorytet, tym większe pozycji w drzewie.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Jeśli występuje ten podklucz Pozycja węzła głównego jest kontrolowana przez okno dialogowe Ustawienia dewelopera. Na przykład  
  
 DeveloperActivity REG_SZ VC#  
  
 Wskazuje, że Visual C# będą węzeł główny Jeśli ustawiono program Visual Studio na [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] rozwoju. W przeciwnym razie będzie elementem podrzędnym **inne języki**.  
  
##### <a name="folder"></a>Folder  
 Jeśli występuje ten podklucz węzeł główny staje się elementem podrzędnym określonego folderu. Zostanie wyświetlona lista możliwych folderów w kluczu  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Na przykład zapis projektów bazy danych ma klucz Folder, który odpowiada wpisowi inne typy projektów PseudoFolders. Tak, to w **typów projektów** drzewie **projektów bazy danych** będzie elementem podrzędnym **inne typy projektów**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Węzły podrzędne typu projektu i plików .vstdir  
 Położenie węzłów podrzędnych w **typów projektów** drzewa następuje po hierarchii folderów w folderach ProjectTemplates. Dla szablonów maszyny (**zainstalowane szablony programu Visual Studio**), Typowa lokalizacja to \Program Files\Microsoft 14.0\Common7\IDE\ProjectTemplates\ programu Visual Studio i szablony użytkownika (**Moje szablony**), Typowa lokalizacja to \My Studio 14.0\Templates\ProjectTemplates\\. Hierarchie folderów z tymi dwiema lokalizacjami są scalane, tworząc **typów projektów** drzewa.  
  
 Dla programu Visual Studio przy użyciu języka C# dla deweloperów ustawień **typów projektów** drzewa wygląda następująco:  
  
 ![Typy projektów](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Odpowiedni folder ProjectTemplates wygląda następująco:  
  
 ![Project Templates](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Gdy **nowy projekt** zostanie otwarte okno dialogowe [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przechodzi przez ProjectTemplates folder i zostaje odtworzony strukturę w **typów projektów** drzewa z niektórych zmian:  
  
-   Węzeł główny na **typów projektów** drzewa jest określana przez szablon aplikacji.  
  
-   Nazwa węzła może być lokalizowana i może zawierać znaków specjalnych.  
  
-   Można zmienić kolejność sortowania.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Znajdowanie węzeł główny dla typu projektu  
 Gdy program Visual Studio przechodzi przez foldery ProjectTemplates, otworzy wszystkie pliki zip i wyodrębnia pliki vstemplate. Plik .vstemplate używa XML do opisu szablonu aplikacji. Aby uzyskać więcej informacji, zobacz [Generowanie nowego projektu: Za kulisami, część dwóch](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 \<ProjectType > tag Określa typ projektu dla aplikacji. Na przykład plik \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip zawiera plik EmptyProject.vstemplate, który zawiera ten tag:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > tag, a nie podfolderu w folderze ProjectTemplates określa węzeł główny aplikacji w **typów projektów** drzewa. W tym przykładzie Windows CE aplikacji zostanie wyświetlony w obszarze **Visual C#** węzła głównego, a nawet wtedy, gdy zostały można przenieść folderu WindowsCE do folderu języka Visual Basic, Windows CE aplikacje nadal będzie pojawiają się w obszarze  **Visual C#** węzła głównego.  
  
##### <a name="localizing-the-node-name"></a>Lokalizowanie nazwy węzła  
 Gdy program Visual Studio przechodzi przez foldery ProjectTemplates, sprawdza, czy wszystkie pliki .vstdir, które znajdzie. Plik .vstdir jest plikiem XML, które kontrolują wygląd typ projektu w **nowy projekt** okno dialogowe. W pliku .vstdir użyj \<LocalizedName > tag, aby nazwa **typów projektów** węzła.  
  
 Na przykład plik \CSharp\Database\TemplateIndex.vstdir zawiera ten tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Ta opcja określa satelitarnej biblioteki DLL i identyfikator zasobu ciągu zlokalizowane nazwy węzła głównego, w tym przypadku **bazy danych**. Zlokalizowana nazwa może zawierać znaków specjalnych, które nie są dostępne dla nazwy folderów, takie jak **.NET**.  
  
 Jeśli nie \<LocalizedName > tag jest obecny, typ projektu jest nazwany przez sam folder, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Znajdowanie porządek sortowania dla typu projektu  
 Aby określić kolejność sortowania typów projektów, należy użyć plików .vstdir \<SortOrder > tag.  
  
 Na przykład plik \CSharp\Windows\Windows.vstdir zawiera ten tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Plik \CSharp\Database\TemplateIndex.vstdir ma tag z większą wartością:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Im mniejsza liczba w \<SortOrder > tag, tym większe pozycji w drzewie, więc **Windows** węzeł pojawi się powyżej **bazy danych** w węźle **typów projektów**  drzewa.  
  
 Jeśli nie \<SortOrder > tag jest określona dla typu projektu pojawiają się one w kolejności alfabetycznej, zgodnie z wszelkich typów projektów, które zawierają \<SortOrder > specyfikacji.  
  
 Należy pamiętać, że nie ma żadnych plików .vstdir w folderze Moje dokumenty (**Moje szablony**) folderów. Nazwy typów projektu aplikacji użytkownika nie są lokalizowane i są wyświetlane w kolejności alfabetycznej.  
  
#### <a name="a-quick-review"></a>Szybki przegląd  
 Zmodyfikujmy **nowy projekt** okna dialogowego pole, a następnie utwórz nowy szablon projektu użytkownika.  
  
1. Dodaj obiekt MyProjectNode podfolderu do folderu 14.0\Common7\IDE\ProjectTemplates\CSharp programu Visual Studio \Program Files\Microsoft.  
  
2. Utwórz plik MyProject.vstdir w folderze Obiekt MyProjectNode za pomocą dowolnego edytora tekstów.  
  
3. Dodaj następujące wiersze do pliku .vstdir:  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Zapisz i zamknij plik .vstdir.  
  
5. Utwórz plik MyProject.vstemplate w folderze Obiekt MyProjectNode za pomocą dowolnego edytora tekstów.  
  
6. Dodaj następujące wiersze do pliku .vstemplate:  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. Zapisz plik the.vstemplate i zamknij Edytor.  
  
8. Wyślij plik .vstemplate do nowego folderu MyProjectNode\MyProject.zip skompresowany.  
  
9. W oknie wiersza polecenia programu Visual Studio wpisz:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Otwórz program Visual Studio.  
  
10. Otwórz **nowy projekt** okna dialogowego pole, a następnie rozwiń węzeł **Visual C#** węzeł projektu.  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **Obiekt MyProjectNode** jest wyświetlany jako węzeł podrzędny programu Visual C# tuż pod węzeł Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie nowego projektu: Kulisami część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
