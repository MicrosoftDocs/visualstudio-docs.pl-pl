---
title: 'Nowa generacja projektu: pod okapem, część jednej | Microsoft Docs'
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
ms.openlocfilehash: 6f26c093f09cd5b7b99f00ee69a81be99c769e2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184144"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generowanie nowego projektu: szczegółowe informacje (część pierwsza)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kiedykolwiek myślisz, jak utworzyć własny typ projektu? Zastanawiasz się, co faktycznie się dzieje podczas tworzenia nowego projektu? Przyjrzyjmy się pod okap i zobacz, co naprawdę się dzieje.  
  
 Istnieje kilka zadań, które program Visual Studio koordynuje:  
  
- Wyświetla drzewo wszystkich dostępnych typów projektów.  
  
- Zostanie wyświetlona lista szablonów aplikacji dla każdego typu projektu i umożliwia wybranie jednego z nich.  
  
- Zbiera informacje o projekcie dla aplikacji, takie jak nazwa projektu i ścieżka.  
  
- Przekazuje te informacje do fabryki projektu.  
  
- Generuje elementy projektu i foldery w bieżącym rozwiązaniu.  
  
## <a name="the-new-project-dialog-box"></a>Okno dialogowe Nowy projekt  
 Wszystko zaczyna się po wybraniu typu projektu dla nowego projektu. Zacznijmy od kliknięcia przycisku **Nowy projekt** w menu **plik** . Pojawi się okno dialogowe **Nowy projekt** , które wygląda następująco:  
  
 ![Okno dialogowe Nowy projekt](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Przyjrzyjmy się temu bliżej. Drzewo **typy projektów** zawiera listę różnych typów projektów, które można utworzyć. Po wybraniu typu projektu, takiego jak **Visual C#**, zobaczysz listę szablonów aplikacji, które ułatwią rozpoczęcie pracy. **Zainstalowane szablony programu Visual Studio** są instalowane przez program Visual Studio i są dostępne dla każdego użytkownika komputera. Nowe szablony, które tworzysz lub zbierasz, można dodać do **moich szablonów** i są dostępne tylko dla Ciebie.  
  
 Po wybraniu szablonu, takiego jak **aplikacja systemu Windows**, w oknie dialogowym pojawi się opis typu aplikacji. w tym przypadku **projekt służący do tworzenia aplikacji z interfejsem użytkownika systemu Windows**.  
  
 W dolnej części okna dialogowego **Nowy projekt** zobaczysz kilka kontrolek, które zbierają więcej informacji. Kontrolki, które widzisz, zależą od typu projektu, ale zazwyczaj zawierają pole tekstowe **Nazwa** projektu, pole tekstowe **lokalizacji** i powiązanego przycisku **przeglądania** oraz pole tekstowe **Nazwa rozwiązania** i powiązane **katalogi tworzenia dla rozwiązania** .  
  
## <a name="populating-the-new-project-dialog-box"></a>Zapełnianie okna dialogowego Nowy projekt  
 Gdzie okno dialogowe **Nowy projekt** otrzymuje informacje z? W tym miejscu istnieją dwa mechanizmy, z których jeden z nich jest przestarzały. Okno dialogowe **Nowy projekt** łączy i wyświetla informacje uzyskane z obu mechanizmów.  
  
 Starsza (przestarzała) Metoda używa wpisów rejestru systemu i plików. vsdir. Ten mechanizm jest uruchamiany, gdy program Visual Studio jest otwarty. Nowsza metoda używa plików. vstemplate. Ten mechanizm jest uruchamiany po zainicjowaniu programu Visual Studio, na przykład przez uruchomienie  
  
```  
devenv /setup  
```  
  
 lub  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Typy projektów  
 Pozycja i nazwy węzłów głównych **typu projektu** , takich jak **Visual C#** i **inne języki**, są określane przez wpisy rejestru systemowego. Organizacja węzłów podrzędnych, taka jak **baza danych** i **urządzenie inteligentne**, odzwierciedla hierarchię folderów zawierających odpowiednie pliki. vstemplate. Najpierw przyjrzyjmy się węzłom głównym.  
  
#### <a name="project-type-root-nodes"></a>Węzły główne typu projektu  
 Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest inicjowany, przechodzi podklucze rejestru systemowego HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\14.0\NewProjectTemplates\TemplateDirs, aby kompilować i nazwać węzły główne drzewa **typów projektu** . Te informacje są przechowywane w pamięci podręcznej do późniejszego użycia. Spójrz na klucz TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1. Każdy wpis jest identyfikatorem GUID pakietu VSPackage. Nazwa podklucza (/1) jest ignorowana, ale jego obecność wskazuje, że jest to węzeł główny **typu projektu** . Węzeł główny może z kolei mieć kilka podkluczy kontrolujących jego wygląd w drzewie **typów projektu** . Przyjrzyjmy się niektórym z nich.  
  
##### <a name="default"></a>(Domyślnie)  
 Jest to identyfikator zasobu zlokalizowanego ciągu, który nazywa węzeł główny. Zasób ciągu znajduje się w satelickiej bibliotece DLL wybranej przez identyfikator GUID pakietu VSPackage.  
  
 W przykładzie identyfikator GUID pakietu VSPackage to  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 i identyfikator zasobu (wartość domyślna) węzła głównego (/1) jest #2345  
  
 Jeśli szukasz identyfikatora GUID w kluczu pobliskich pakietów i sprawdzisz podklucz SatelliteDll, możesz znaleźć ścieżkę zestawu zawierającego zasób ciągu:  
  
 \<Visual Studio installation path>\VC # \VCSPackages\1033\csprojui.dll  
  
 Aby to sprawdzić, otwórz Eksploratora plików i przeciągnij csprojui.dll do katalogu programu Visual Studio. Tabela ciągów pokazuje, że #2345 zasobów zawiera **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Określa położenie węzła głównego w drzewie **typów projektu** .  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Im mniejsza liczba priorytetów, tym większa pozycja w drzewie.  
  
##### <a name="developeractivity"></a>Programowanie  
 Jeśli ten podklucz jest obecny, położenie węzła głównego jest kontrolowane przez okno dialogowe Ustawienia dewelopera. Przykład:  
  
 Programowanie REG_SZ VC #  
  
 wskazuje, że Visual C# będzie węzłem głównym, jeśli program Visual Studio jest ustawiony na potrzeby [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] programowania. W przeciwnym razie będzie to węzeł podrzędny **innych języków**.  
  
##### <a name="folder"></a>Folder  
 Jeśli ten podklucz jest obecny, węzeł główny będzie węzłem podrzędnym określonego folderu. W kluczu zostanie wyświetlona lista możliwych folderów  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Na przykład wpis projekty bazy danych ma klucz folderu pasujący do innego typu projektu w PseudoFolders. Dlatego w drzewie **typów projektu** **projekty bazy danych** będą węzłem podrzędnym **innych typów projektów**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Węzły podrzędne typu projektu i pliki. vstdir  
 Pozycja węzłów podrzędnych w drzewie **typów projektu** jest zgodna z hierarchią folderów w folderach ProjectTemplates. W przypadku szablonów komputera (**szablonów zainstalowanych w programie Visual Studio**) typowa lokalizacja to \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\ i szablonów użytkowników (**Moje szablony**) — typowa lokalizacja to \Moje Documents\Visual Studio 14.0 \ Templates\ProjectTemplates \\ . Hierarchie folderów z tych dwóch lokalizacji są scalane w celu utworzenia drzewa **typów projektu** .  
  
 W przypadku programu Visual Studio z ustawieniami dewelopera C# drzewo **typów projektu** wygląda następująco:  
  
 ![Typy projektów](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Odpowiedni folder ProjectTemplates wygląda następująco:  
  
 ![Szablony projektów](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Gdy zostanie otwarte okno dialogowe **Nowy projekt** , przejdziesz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do folderu ProjectTemplates i utworzysz jego strukturę w drzewie **typów projektu** z pewnymi zmianami:  
  
- Węzeł główny w drzewie **typów projektu** jest określany przez szablon aplikacji.  
  
- Nazwa węzła może być lokalizowana i może zawierać znaki specjalne.  
  
- Kolejność sortowania można zmienić.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Znajdowanie węzła głównego dla typu projektu  
 Gdy program Visual Studio przechodzi przez foldery ProjectTemplates, otwiera wszystkie pliki zip i wyodrębnia wszystkie pliki. vstemplate. Plik. vstemplate używa kodu XML do opisania szablonu aplikacji. Aby uzyskać więcej informacji, zobacz temat [Nowa generacja projektu: pod okapem, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 \<ProjectType>Tag określa typ projektu dla aplikacji. Na przykład plik \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip zawiera plik EmptyProject. vstemplate, który ma następujący Tag:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType>Tag, a nie podfolder w folderze ProjectTemplates, określa węzeł główny aplikacji w drzewie **typów projektu** . W przykładzie Windows CE aplikacje pojawią się w węźle głównym **Visual C#** , a nawet jeśli przeniesiesz folder WindowsCE do folderu VisualBasic, aplikacje Windows CE nadal będą widoczne w węźle głównym **Visual C#** .  
  
##### <a name="localizing-the-node-name"></a>Lokalizowanie nazwy węzła  
 Gdy program Visual Studio przechodzi przez foldery ProjectTemplates, analizuje on wszystkie znalezione pliki. vstdir. Plik. vstdir jest plikiem XML, który steruje wyglądem typu projektu w oknie dialogowym **Nowy projekt** . W pliku. vstdir Użyj \<LocalizedName> znacznika, aby nazwać węzeł **typy projektu** .  
  
 Na przykład plik \CSharp\Database\TemplateIndex.vstdir zawiera następujący Tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Określa to satelitarną bibliotekę DLL i identyfikator zasobu zlokalizowanego ciągu, który nazywa węzeł główny, w tym przypadku **bazy danych**. Zlokalizowana nazwa może zawierać znaki specjalne, które nie są dostępne dla nazw folderów, takich jak **.NET**.  
  
 Jeśli żaden \<LocalizedName> tag nie jest obecny, typ projektu jest nazwany przez samego folderu, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Znajdowanie kolejności sortowania dla typu projektu  
 Aby określić kolejność sortowania typu projektu, pliki VSTDIR używają \<SortOrder> znacznika.  
  
 Na przykład plik \CSharp\Windows\Windows.vstdir zawiera następujący Tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Plik \CSharp\Database\TemplateIndex.vstdir ma tag o większej wartości:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Im mniejsza liczba w \<SortOrder> znaczniku, tym większa pozycja w drzewie, więc węzeł **systemu Windows** jest wyświetlany w drzewie **typów projektu** niż węzeł **bazy danych** .  
  
 Jeśli żaden \<SortOrder> tag nie jest określony dla typu projektu, pojawia się w kolejności alfabetycznej po każdym typie projektu, który zawiera \<SortOrder> specyfikacje.  
  
 Zwróć uwagę, że w folderach Moje dokumenty (**Moje szablony**) nie ma plików VSTDIR. Nazwy typów projektów aplikacji użytkownika nie są zlokalizowane i są wyświetlane w kolejności alfabetycznej.  
  
#### <a name="a-quick-review"></a>Krótki przegląd  
 Zmodyfikujmy okno dialogowe **Nowy projekt** i utworzysz nowy szablon projektu użytkownika.  
  
1. Dodaj podfolder MyProjectNode do folderu \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp.  
  
2. Utwórz plik WebProject. vstdir w folderze MyProjectNode przy użyciu dowolnego edytora tekstu.  
  
3. Dodaj te wiersze do pliku VSTDIR:  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Zapisz i zamknij plik. vstdir.  
  
5. Utwórz plik WebProject. vstemplate w folderze MyProjectNode przy użyciu dowolnego edytora tekstu.  
  
6. Dodaj te wiersze do pliku vstemplate:  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. Zapisz plik. vstemplate i Zamknij Edytor.  
  
8. Wyślij plik vstemplate do nowego folderu skompresowanego MyProjectNode\MyProject.zip.  
  
9. W oknie wiersza polecenia programu Visual Studio wpisz:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Otwórz program Visual Studio.  
  
10. Otwórz okno dialogowe **Nowy projekt** i rozwiń węzeł projektu **Visual C#** .  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **MyProjectNode** pojawia się jako węzeł podrzędny języka Visual C# tuż pod węzłem systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie nowego projektu: szczegółowe informacje (część druga)](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
