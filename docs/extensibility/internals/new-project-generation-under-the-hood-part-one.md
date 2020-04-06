---
title: 'Nowa generacja projektów: Pod maską, część pierwsza | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707054"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generowanie nowego projektu: za kulisami, część pierwsza
Czy kiedykolwiek myślałeś o tym, jak stworzyć własny typ projektu? Zastanawiasz się, co tak naprawdę dzieje się podczas tworzenia nowego projektu? Rówmy się pod maskę i zobaczmy, co tak naprawdę się dzieje.

 Istnieje kilka zadań, które program Visual Studio koordynuje dla Ciebie:

- Wyświetla drzewo wszystkich dostępnych typów projektów.

- Wyświetla listę szablonów aplikacji dla każdego typu projektu i umożliwia wybranie jednego.

- Zbiera informacje o projekcie dla aplikacji, takie jak nazwa projektu i ścieżka.

- Przekazuje te informacje do fabryki projektu.

- Generuje elementy projektu i foldery w bieżącym rozwiązaniu.

## <a name="the-new-project-dialog-box"></a>Okno dialogowe Nowy projekt
 Wszystko zaczyna się po wybraniu typu projektu dla nowego projektu. Zacznijmy od kliknięcia przycisku **Nowy projekt** w menu **Plik.** Zostanie wyświetlone okno dialogowe **Nowy projekt,** wyglądające mniej więcej tak:

 ![Okno dialogowe Nowy projekt](../../extensibility/internals/media/newproject.gif "Nowyprojekt")

 Przyjrzyjmy się temu bliżej. **Drzewo Typy projektu** zawiera listę różnych typów projektów, które można utworzyć. Po wybraniu typu projektu, takiego jak **System Windows w języku Visual C#,** zostanie wyświetlona lista szablonów aplikacji na początek. **Zainstalowane szablony programu Visual Studio** są instalowane przez program Visual Studio i są dostępne dla każdego użytkownika komputera. Nowe szablony, które tworzysz lub zbierasz, mogą być dodawane do **moich szablonów** i są dostępne tylko dla Ciebie.

 Po wybraniu szablonu, takiego jak **Aplikacja systemu Windows,** w oknie dialogowym pojawi się opis typu aplikacji; w tym przypadku **Projekt do tworzenia aplikacji z interfejsem użytkownika systemu Windows**.

 U dołu okna dialogowego **Nowy projekt** zobaczysz kilka formantów, które zbierają więcej informacji. Wyświetlane formanty zależą od typu projektu, ale zazwyczaj obejmują pole tekstowe **Nazwa** projektu, pole **tekstowe** **Lokalizacja** i powiązany przycisk Przeglądaj oraz pole tekstowe **Nazwa rozwiązania** i powiązane pole wyboru **Utwórz katalog dla rozwiązania.**

## <a name="populating-the-new-project-dialog-box"></a>Wypełnianie okna dialogowego Nowy projekt
 Skąd okno dialogowe **Nowy projekt** otrzymuje informacje? Istnieją dwa mechanizmy w pracy tutaj, jeden z nich przestarzały. Okno dialogowe **Nowy projekt** łączy i wyświetla informacje uzyskane z obu mechanizmów.

 Starsza (przestarzała) metoda używa wpisów rejestru systemowego i plików vsdir. Ten mechanizm jest uruchamiany po otwarciu programu Visual Studio. Nowsza metoda używa plików vstemplate. Ten mechanizm jest uruchamiany, gdy program Visual Studio jest inicjowany, na przykład przez

```
devenv /setup
```

 lub

```
devenv /installvstemplates
```

### <a name="project-types"></a>Project Types (Typy projektów)
 Położenie i nazwy węzłów głównych **typów projektu,** takich jak **Visual C#** i **Inne języki,** są określane przez wpisy rejestru systemowego. Organizacja węzłów podrzędnych, takich jak **Baza danych** i **Urządzenie inteligentne,** odzwierciedla hierarchię folderów zawierających odpowiednie pliki vstemplate. Przyjrzyjmy się najpierw węzłom głównym.

#### <a name="project-type-root-nodes"></a>Węzły główne typu projektu
 Po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zainicjowaniu przechodzi przez podklu skróty klucza rejestru systemowego HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs, aby utworzyć i nazwać węzły główne drzewa **Typy projektu.** Te informacje są buforowane do późniejszego użycia. Spójrz na templateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}\\/1 klucz. Każdy wpis jest identyfikatorem GUID VSPackage. Nazwa podklucza (/1) jest ignorowana, ale jego obecność wskazuje, że jest to węzeł główny **typów projektu.** Węzeł główny może z kolei mieć kilka podkluczów, które kontrolują jego wygląd w drzewie **typy projektu.** Spójrzmy na niektóre z nich.

##### <a name="default"></a>(Domyślnie)
 Jest to identyfikator zasobu zlokalizowanego ciągu, który nazywa węzeł główny. Zasób ciągu znajduje się w satelicie DLL wybrany przez VSPackage GUID.

 W tym przykładzie identyfikator GUID VSPackage jest

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 a identyfikator zasobu (wartość domyślna) węzła głównego (/1) jest #2345

 Jeśli wyszukujesz identyfikator GUID w pobliskim kluczu Packages i zbadasz podklucz SatelliteDll, możesz znaleźć ścieżkę zestawu zawierającego zasób ciągu:

 \<Ścieżka instalacji programu Visual Studio>\VC#\VCSPackages\1033\csprojui.dll

 Aby to sprawdzić, otwórz Eksploratora plików i przeciągnij plik csprojui.dll do katalogu programu Visual Studio.To verify this, open the File Explorer and drag csprojui.dll into the Visual Studio directory.to verify this, open the File Explorer and drag csprojui.dll into the Visual Studio directory.to. Tabela ciągów pokazuje, że #2345 zasobu ma podpis **Visual C#**.

##### <a name="sortpriority"></a>SortPriority (SortPriority)
 Określa położenie węzła głównego w drzewie **Typy projektu.**

 SortPriority REG_DWORD 0x00000014 (20)

 Im mniejsza liczba priorytetów, tym wyższa pozycja w drzewie.

##### <a name="developeractivity"></a>Działalność dewelopera
 Jeśli ten podklucz jest obecny, położenie węzła głównego jest kontrolowane przez okno dialogowe Ustawienia dewelopera. Na przykład:

 DeveloperActivity REG_SZ VC #

 wskazuje, że visual C# będzie węzłem głównym, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] jeśli visual studio jest ustawiony na rozwój. W przeciwnym razie będzie to węzeł podrzędny **innych języków**.

##### <a name="folder"></a>Folder
 Jeśli ten podklucz jest obecny, węzeł główny staje się węzłem podrzędnym określonego folderu. Pod klawiszem pojawi się lista możliwych folderów

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Na przykład wpis Projekty bazy danych ma klucz folderu, który pasuje do wpisu Inne typy projektów w PseudoFolders. Tak więc w drzewie **Typy projektów** **projekty bazy danych** będą węzłem podrzędnym innych typów **projektów.**

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Typ projektu węzły podrzędne i pliki vstdir
 Położenie węzłów podrzędnych w drzewie **Typy projektu** następuje zgodnie z hierarchią folderów w folderach ProjectTemplates. W przypadku szablonów maszyn **(zainstalowane szablony programu Visual Studio)** typową lokalizacją jest \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ oraz dla szablonów użytkowników (**Moje szablony**), typową lokalizacją jest \Moje dokumenty\Visual Studio 14.0\Templates\ProjectTemplates\\. Hierarchie folderów z tych dwóch lokalizacji są scalane w celu utworzenia drzewa **typy projektu.**

 W programie Visual Studio z ustawieniami dewelopera języka C# drzewo **typów projektu** wygląda mniej więcej tak:

 ![Project Types (Typy projektów)](../../extensibility/internals/media/projecttypes.png "Typy projektu")

 Odpowiedni folder ProjectTemplates wygląda następująco:

 ![Szablony projektów](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates (Placki projektowe)")

 Po otwarciu okna dialogowego **Nowy projekt** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przechodzi przez folder ProjectTemplates i odtwarza jego strukturę w drzewie **Typy projektu** z pewnymi zmianami:

- Węzeł główny w drzewie **Typy projektu** jest określany przez szablon aplikacji.

- Nazwa węzła może być zlokalizowana i może zawierać znaki specjalne.

- Kolejność sortowania może zostać zmieniona.

##### <a name="finding-the-root-node-for-a-project-type"></a>Znajdowanie węzła głównego dla typu projektu
 Gdy program Visual Studio przechodzi przez foldery ProjectTemplates, otwiera wszystkie pliki zip i wyodrębnia wszystkie pliki vstemplate. Plik vstemplate używa xml do opisania szablonu aplikacji. Aby uzyskać więcej informacji, zobacz [Nowa generacja projektu: Pod maską, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 \<Tag> ProjectType określa typ projektu dla aplikacji. Na przykład plik \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip zawiera plik EmptyProject.vstemplate zawierający ten znacznik:

```
<ProjectType>CSharp</ProjectType>
```

 Znacznik \<> ProjectType, a nie podfolder w folderze ProjectTemplates, określa węzeł główny aplikacji w drzewie **typy projektu.** W tym przykładzie aplikacje CE systemu Windows pojawią się w węźle głównym **języka Visual C#,** a nawet jeśli folder WindowsCE zostanie przeniesione do folderu VisualBasic, aplikacje systemu Windows CE nadal będą wyświetlane w węźle głównym **języka Visual C#.**

##### <a name="localizing-the-node-name"></a>Lokalizowanie nazwy węzła
 Gdy program Visual Studio przechodzi przez foldery ProjectTemplates, sprawdza wszystkie pliki vstdir znaleźć. Plik vstdir to plik XML, który steruje wyglądem typu projektu w oknie dialogowym **Nowy projekt.** W pliku vstdir użyj \<tagu> LocalizedName, aby nadać nazwę węzłowi **Typy projektu.**

 Na przykład plik \CSharp\Database\TemplateIndex.vstdir zawiera ten tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Określa to bibliotekę DLL satelity i identyfikator zasobu zlokalizowanego ciągu, który nazywa węzeł główny, w tym przypadku **bazą danych**. Zlokalizowana nazwa może zawierać znaki specjalne, które nie są dostępne dla nazw folderów, takie jak **.NET**.

 Jeśli \<nie ma znacznika> LocalizedName, typ projektu jest nazwany przez sam folder **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Znajdowanie kolejności sortowania dla typu projektu
 Aby określić kolejność sortowania typu projektu, pliki \<vstdir używają znacznika SortOrder>.

 Na przykład plik \CSharp\Windows\Windows.vstdir zawiera ten znacznik:

```
<SortOrder>5</SortOrder>
```

 Plik \CSharp\Database\TemplateIndex.vstdir ma znacznik o większej wartości:

```
<SortOrder>5000</SortOrder>
```

 Im mniejsza liczba \<w znaczniku SortOrder>, tym wyższa pozycja w drzewie, więc węzeł **systemu Windows** jest wyświetlany wyżej niż węzeł **Baza danych** w drzewie **Typy projektu.**

 Jeśli \<dla typu projektu nie określono znacznika SortOrder>, jest on wyświetlany w \<kolejności alfabetycznej zgodnie z wszelkimi typami projektów zawierającymi specyfikacje sortorder>.

 Należy zauważyć, że w folderach Moje dokumenty **(Moje szablony)** nie ma żadnych plików vstdir. Nazwy typów projektu aplikacji użytkownika nie są zlokalizowane i są wyświetlane w kolejności alfabetycznej.

#### <a name="a-quick-review"></a>Szybki przegląd
 Zmodyfikujmy okno dialogowe **Nowy projekt** i utwórz nowy szablon projektu użytkownika.

1. Dodaj podfolder MyProjectNode do folderu \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp folder.

2. Utwórz plik MyProject.vstdir w folderze MyProjectNode przy użyciu dowolnego edytora tekstu.

3. Dodaj te wiersze do pliku vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Zapisz i zamknij plik vstdir.

5. Utwórz plik MyProject.vstemplate w folderze MyProjectNode przy użyciu dowolnego edytora tekstu.

6. Dodaj te wiersze do pliku vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Zapisz plik.vstemplate i zamknij edytor.

8. Wyślij plik vstemplate do nowego skompresowanego folderu MyProjectNode\MyProject.zip.

9. W oknie polecenia programu Visual Studio wpisz:

    ```
    devenv /installvstemplates
    ```

   Otwórz program Visual Studio.

10. Otwórz okno dialogowe **Nowy projekt** i rozwiń węzeł projektu **Visual C#.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** pojawia się jako węzeł podrzędny języka Visual C# tuż pod węzłem systemu Windows.

## <a name="see-also"></a>Zobacz też
- [Generowanie nowego projektu: za kulisami, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
