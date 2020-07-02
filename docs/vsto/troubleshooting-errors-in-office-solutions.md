---
title: Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
ms.date: 02/02/2017
ms.topic: troubleshooting
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d73dadd10342d3616291fb93efbb447bd7ecaee
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537322"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
  Podczas opracowywania rozwiązań pakietu Office w programie Visual Studio mogą wystąpić problemy związane z wykonywaniem następujących zadań:

- [Twórz, uaktualniaj i otwieraj projekty](#creating)

- [Korzystanie z projektantów](#designers)

- [Pisanie kodu](#code)

- [Kompiluj projekty](#building)

- [Debuguj projekty](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a>Twórz, uaktualniaj i otwieraj projekty
 Podczas tworzenia lub otwierania projektów pakietu Office mogą wystąpić następujące błędy.

### <a name="the-project-cannot-be-created"></a>Nie można utworzyć projektu
 Wystąpił błąd podczas próby utworzenia lub otwarcia projektu pakietu Office, ale program Visual Studio nie ma wystarczających informacji, aby określić przyczynę. Spróbuj zamknąć projekt, Zamknij program Visual Studio i zacznij od nowa.

 Jeśli próbujesz utworzyć projekt na poziomie dokumentu, możliwe jest, że inny dokument o takiej samej nazwie jak dokument w nowym projekcie jest już otwarty w programie Excel lub Word. Upewnij się, że wszystkie inne wystąpienia programu Excel lub Word są zamknięte.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Właściwości kontrolki są tracone podczas tworzenia nowego projektu na podstawie dokumentu z istniejącego projektu
 Jeśli utworzysz nowy projekt pakietu Office oparty na dokumencie z istniejącego projektu, właściwości formantów, które znajdują się w dokumencie, nie są kopiowane do nowego projektu. Należy ręcznie zresetować właściwości dla wszystkich istniejących kontrolek. Alternatywnie można zachować właściwości kontrolki, tworząc kopię istniejącego projektu, zamiast tworzyć nowy projekt lub ładując istniejący projekt do nowego rozwiązania (w Projektancie) i kopiując i wklejając kontrolki z istniejącego dokumentu do nowego dokumentu.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Błędy podczas tworzenia projektu skoroszytu programu Excel na podstawie istniejącego skoroszytu
 Jeśli utworzysz nowy projekt skoroszytu programu Excel na podstawie istniejącego skoroszytu, może zostać wyświetlona kombinacja następujących błędów.

 W programie Excel: "ostrzeżenie dotyczące prywatności: ten dokument zawiera makra, kontrolki ActiveX, informacje o pakiecie rozszerzenia XML lub składniki sieci Web. Mogą one zawierać informacje osobiste, które nie mogą zostać usunięte przez Inspektora dokumentów ".

 W programie Visual Studio: "nie można poprawnie załadować projektanta".

 Te błędy mogą wystąpić przy próbie utworzenia projektu opartego na skoroszycie, do którego zostały usunięte dane osobowe za pomocą Inspektora dokumentów. Aby uniknąć tego błędu, przed utworzeniem projektu wykonaj następujące czynności.

1. Otwórz skoroszyt w programie Excel.

2. W programie Excel otwórz Centrum zaufania.

3. Na karcie **Opcje prywatności** wyczyść pole wyboru **Usuń dane osobowe z właściwości pliku przy zapisywaniu** .

4. Zapisz skoroszyt i Zamknij program Excel.

### <a name="cannot-open-a-project-after-migration"></a>Nie można otworzyć projektu po migracji
 Po przeprowadzeniu migracji rozwiązania pakietu Office do Microsoft Office 2010 nie można otworzyć tego projektu na komputerze deweloperskim z zainstalowanym systemem Microsoft Office 2007. Mogą pojawić się następujące błędy.

 "Co najmniej jeden projekt w rozwiązaniu nie został poprawnie załadowany. Aby uzyskać szczegółowe informacje, zobacz Okno Dane wyjściowe ".

 "Nie można utworzyć projektu, ponieważ aplikacja skojarzona z tym typem projektu nie jest zainstalowana na tym komputerze. Należy zainstalować aplikację Microsoft Office, która jest skojarzona z tym typem projektu ".

 Aby rozwiązać ten problem, edytuj plik *. vbproj* lub *. csproj* . W przypadku projektu programu Word Zamień HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" na HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}". W przypadku projektu programu Excel Zastąp ciąg HostPackage = "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" atrybutem HostPackage = "{825100CF-0BA7-47EA-A084-DCF3308DAF74}". W przypadku projektu programu Outlook Zastąp ciąg HostPackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" atrybutem HostPackage = "{20A848B8-E01F-4801-962E-25DB0FF57389}".

 Alternatywnie upewnij się, że migrowane projekty są otwierane tylko na komputerach deweloperskich z zainstalowanym Microsoft Office 2010.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Błędy uaktualnionych projektów na poziomie dokumentu pakietu Office 2003, które zawierają kontrolki Windows Forms
 W przypadku uaktualniania projektu na poziomie dokumentu Microsoft Office 2003, a dokument zawiera kontrolki Windows Forms, uaktualniony projekt może mieć błędy kompilacji lub czasu wykonywania. Aby uniknąć tego problemu, zainstaluj program Visual Studio 2005 Tools for Office Second Edition Runtime na komputerze deweloperskim przed uaktualnieniem projektu. Ta wersja środowiska uruchomieniowego jest dostępna jako pakiet redystrybucyjny z centrum pobierania Microsoft w witrynie [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

 Po zakończeniu uaktualniania projektu można odinstalować program Visual Studio 2005 Tools for Office Second Edition Runtime z komputera deweloperskiego, jeśli nie jest on używany przez inne rozwiązania pakietu Office.

## <a name="use-the-designers"></a><a name="designers"></a>Korzystanie z projektantów
 Podczas pracy z dokumentem, skoroszytem lub projektantem arkusza w projektach na poziomie dokumentu mogą wystąpić następujące błędy.

### <a name="designer-failed-to-load-correctly"></a>Nie można poprawnie załadować projektanta
 Program Visual Studio nie może otworzyć projektanta w następujących przypadkach:

- Program Excel lub Word jest już otwarty i wyświetla modalne okno dialogowe. Aby otworzyć projektanta, sprawdź, czy w programie Excel lub Word jest otwarte modalne okno dialogowe, a następnie zamknij wszystkie otwarte modalne okna dialogowe. Jeśli nie ma otwartych modalnych okien dialogowych, może istnieć inne działanie wymagane przed odpowiedzią programu Excel lub Word.

- Projekt jest obecnie debugowany. Aby otworzyć projektanta, Zatrzymaj lub Zakończ debugowanie.

- Dodatek narzędzi VSTO dla programu Excel zainstalowany na komputerze deweloperskim wyświetla okno dialogowe podczas uruchamiania programu Excel. Aby utworzyć projekt na poziomie dokumentu programu Excel, należy najpierw wyłączyć dodatek VSTO.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Kontrolki są wyświetlane jako czarne prostokąty w dokumencie lub arkuszu
 Jeśli grupujesz formanty w dokumencie lub arkuszu, program Visual Studio nie rozpoznaje już kontrolek. Nie można uzyskać dostępu do zgrupowanych kontrolek w oknie **Właściwości** , które są wyświetlane jako czarne prostokąty w dokumencie lub arkuszu. Aby przywrócić ich funkcjonalność, należy rozgrupować formanty.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Kontrolki w szablonie słowa nie są widoczne w programie Visual Studio
 Jeśli otworzysz szablon programu Word w projektancie programu Visual Studio, formanty na szablonie, które nie znajdują się w wierszu z tekstem, mogą nie być widoczne. Dzieje się tak, ponieważ program Visual Studio otwiera szablony programu Word w widoku **normalnym** . Aby wyświetlić formanty, kliknij menu **Widok** , wskaż polecenie **Microsoft Office widok programu Word** , a następnie kliknij pozycję **Układ wydruku**.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Polecenie Wstaw clipart nie wykonuje żadnych operacji w projektancie programu Visual Studio
 Gdy program Excel lub Word jest otwarty w projektancie programu Visual Studio, kliknięcie przycisku **Przytnij clipart** na karcie **ilustracje** na Wstążce nie powoduje otworzenia **okienka zadań Clipart** . Aby dodać clipart, należy otworzyć kopię skoroszytu lub dokumentu znajdującego się w głównym folderze projektu (a nie kopię znajdującą się w folderze *\Bin* ) poza programem Visual Studio, dodać obiekt clipart, a następnie zapisać skoroszyt lub dokument.

## <a name="write-code"></a><a name="code"></a>Napisz kod
 Podczas pisania kodu w projektach pakietu Office mogą wystąpić następujące błędy.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Niektóre zdarzenia obiektów pakietu Office są niedostępne przy użyciu języka C\#
 W niektórych przypadkach podczas próby uzyskania dostępu do określonego zdarzenia wystąpienia podstawowego zestawu międzyoperacyjnego (PIA) pakietu Office w projekcie Visual C# może zostać wyświetlony błąd kompilatora podobny do poniższego.

 "Niejednoznaczność między elementami" Microsoft. Office. Interop. Excel. _Application. NewWorkbook "i" Microsoft. Office. Interop. Excel. AppEvents_Event. NewWorkbook ""

 Ten błąd oznacza, że próbujesz uzyskać dostęp do zdarzenia, które ma taką samą nazwę jak inna właściwość lub metoda obiektu. Aby uzyskać dostęp do zdarzenia, należy rzutować obiekt na jego *interfejs zdarzenia*.

 Typy PIA pakietu Office ze zdarzeniami implementujących dwa interfejsy: podstawowy interfejs ze wszystkimi właściwościami i metodami oraz interfejsem zdarzenia, który zawiera zdarzenia, które są udostępniane przez obiekt. Te interfejsy zdarzeń używają konwencji nazewnictwa *NazwaObiektu*zdarzenia*n*_Event, takich jak <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> i <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . Jeśli nie możesz uzyskać dostępu do zdarzenia, które oczekujesz znaleźć na obiekcie, rzutowanie obiektu na interfejs zdarzenia.

 Na przykład <xref:Microsoft.Office.Interop.Excel.Application> obiekty mają <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> zdarzenie i <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> Właściwość. Aby obsłużyć <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> zdarzenie, należy rzutować <xref:Microsoft.Office.Interop.Excel.Application> do <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> interfejsu. Poniższy przykład kodu demonstruje, jak to zrobić w projekcie na poziomie dokumentu dla programu Excel.

 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]

 Aby uzyskać więcej informacji na temat interfejsów zdarzeń w usłudze Office zestawów Pia, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12//ms247299(v=office.12)).

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>Nie można odwołać się do klas PIA pakietu Office w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , kod, który odwołuje się do klasy, która jest zdefiniowana w Piau pakietu Office nie zostanie domyślnie skompilowana. Klasy w zestawów Pia używają klasy *NazwaObiektu*konwencji nazewnictwa, takiej jak <xref:Microsoft.Office.Interop.Word.DocumentClass> i <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . Na przykład następujący kod z projektu dodatku VSTO programu Word nie zostanie skompilowany.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Ten kod powoduje następujące błędy kompilacji:

- Visual Basic: "odwołanie do klasy" DocumentClass "jest niedozwolone, gdy jej zestaw jest połączony przy użyciu trybu bez PIA."

- Visual C#: nie można osadzić typu międzyoperacyjnego "Microsoft.Office.Interop.Word.DocumentClass". Zamiast tego użyj odpowiedniego interfejsu ".

  Aby rozwiązać ten problem, należy zmodyfikować kod w celu odwołania się do odpowiedniego interfejsu. Na przykład zamiast odwoływać się do <xref:Microsoft.Office.Interop.Word.DocumentClass> obiektu, odwołuje się do wystąpienia <xref:Microsoft.Office.Interop.Word.Document> interfejsu.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 Projekty, które są przeznaczone dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , automatycznie osadzają domyślnie wszystkie typy międzyoperacyjności z pakietu Office zestawów Pia. Ten błąd kompilacji występuje, ponieważ Wbudowana funkcja typów międzyoperacyjnych działa tylko z interfejsami, a nie klasami. Aby uzyskać więcej informacji na temat interfejsów i klas w zestawów PIA pakietu Office, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)). Aby uzyskać więcej informacji na temat funkcji osadzonych typów międzyoperacyjnych w projektach pakietu Office, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="references-to-office-classes-are-not-recognized"></a>Nie rozpoznano odwołań do klas pakietu Office
 Niektóre nazwy klas, na przykład aplikacje, znajdują się w wielu obszarach nazw, takich jak <xref:Microsoft.Office.Interop.Word> i <xref:System.Windows.Forms> . Z tego powodu instrukcja **Imports** / **using** na początku szablonów projektu zawiera skróconą stałą, na przykład:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]

 To użycie instrukcji **Imports** / **using** wymaga odróżnienia odwołań do klas pakietu Office z kwalifikatorem Word lub Excel, na przykład:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]

 W przypadku korzystania z niekwalifikowanej deklaracji, na przykład:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]

 Mimo że zaimportowano obszar nazw programu Word lub Excel i masz dostęp do wszystkich klas wewnątrz niego, musisz w pełni zakwalifikować wszystkie typy z programem Word lub Excel, aby usunąć niejednoznaczność przestrzeni nazw.

## <a name="build-projects"></a><a name="building"></a>Kompiluj projekty
 Podczas kompilowania projektów pakietu Office mogą wystąpić następujące błędy.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Nie można skompilować projektu na poziomie dokumentu opartego na dokumencie z ograniczonymi uprawnieniami
 Program Visual Studio nie może kompilować projektów na poziomie dokumentu, jeśli dokument ma ograniczone uprawnienia. Jeśli projekt zawiera dokument z ograniczonymi uprawnieniami, projekt nie zostanie skompilowany, a w oknie **Lista błędów** zostanie wyświetlony następujący komunikat.

 "Nie można dodać dostosowania".

 Jeśli chcesz dołączyć dokument z ograniczonymi uprawnieniami, podczas opracowywania i kompilowania rozwiązania Użyj dokumentu bez ograniczeń. Następnie należy zastosować ograniczone uprawnienia do dokumentu w lokalizacji publikowania po opublikowaniu rozwiązania.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Błędy kompilatora występują po usunięciu formantu NamedRange
 Jeśli usuniesz <xref:Microsoft.Office.Tools.Excel.NamedRange> formant z arkusza, który nie jest aktywnym arkuszem w projektancie, kod wygenerowany automatycznie może nie zostać usunięty z projektu i mogą wystąpić błędy kompilatora. Aby upewnić się, że kod został usunięty, należy zawsze zaznaczyć arkusz, który zawiera <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę, aby uczynić go aktywnym arkuszem przed usunięciem formantu. Jeśli automatycznie wygenerowany kod nie jest usuwany po usunięciu kontrolki, można spowodować, że projektant usunie ten kod, aktywując arkusz i wprowadzając zmianę, tak aby arkusz został oznaczony jako zmodyfikowany. Po odbudowaniu projektu kod jest usuwany.

## <a name="debug-projects"></a><a name="debugging"></a>Debuguj projekty
 Podczas debugowania projektów pakietu Office mogą wystąpić następujące błędy.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Monit o odinstalowanie jest wyświetlany podczas publikowania i instalowania rozwiązania na komputerze deweloperskim
 Podczas debugowania rozwiązania pakietu Office może zostać wyświetlony następujący błąd.

 "Dostosowania nie można zainstalować, ponieważ inna wersja jest obecnie zainstalowana i nie można jej uaktualnić z tej lokalizacji".

 Ten błąd oznacza, że wcześniej opublikowano i zainstalowano rozwiązanie pakietu Office na komputerze deweloperskim. Aby zapobiec pojawianiu się komunikatu, przed debugowaniem rozwiązania Odinstaluj rozwiązanie z listy zainstalowanych programów na komputerze. Alternatywnie można utworzyć inne konto użytkownika na komputerze deweloperskim w celu przetestowania instalacji opublikowanego rozwiązania.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projekty na poziomie dokumentu utworzone w lokalizacjach sieciowych UNC nie są uruchamiane z programu Visual Studio
 W przypadku tworzenia projektu na poziomie dokumentu dla programu Excel lub Word w lokalizacji sieciowej UNC należy dodać lokalizację dokumentu do listy zaufanych lokalizacji w programie Excel lub Word. W przeciwnym razie dostosowanie nie zostanie załadowane podczas próby uruchomienia lub debugowania projektu w programie Visual Studio. Aby uzyskać więcej informacji na temat zaufanych lokalizacji, zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Wątki nie są prawidłowo zatrzymane po debugowaniu
 Projekty pakietu Office w programie Visual Studio są zgodne z konwencją nazewnictwa wątków, która umożliwia debugerowi poprawne zamknięcie programu. Jeśli tworzysz wątki w rozwiązaniu, należy nazwać każdy wątek z prefiksem VSTA_, aby upewnić się, że te wątki są prawidłowo obsługiwane po zatrzymaniu debugowania. Na przykład możesz ustawić `Name` Właściwość wątku, który czeka na **VSTA_NetworkListener**zdarzenie sieciowe.

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Nie można uruchomić lub debugować żadnego rozwiązania pakietu Office na komputerze deweloperskim
 Jeśli nie można uruchomić lub opracować projektu pakietu Office na komputerze deweloperskim, może zostać wyświetlony następujący komunikat o błędzie.

 "Nie można załadować dostosowania, ponieważ nie można utworzyć domeny aplikacji".

 Program Visual Studio używa programu Fusion, modułu ładującego zestaw .NET Framework do buforowania zestawów przed załadowaniem rozwiązań pakietu Office. Upewnij się, że program Visual Studio może zapisać w pamięci podręcznej Fusion, i spróbuj ponownie. Aby uzyskać więcej informacji, zobacz [zestawy kopii w tle](/dotnet/framework/app-domains/shadow-copy-assemblies).

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Błąd podczas zatrzymywania debugera w projekcie na poziomie dokumentu po użyciu funkcji Edytuj i Kontynuuj
 Jeśli używasz **Edytuj** i **Kontynuuj** , aby wprowadzić zmiany w kodzie w projekcie na poziomie dokumentu dla programu Excel lub Word, podczas gdy projekt jest w trybie przerwania, po zatrzymaniu debugera można wyświetlić okno dialogowe z następującym komunikatem o błędzie.

 "Zakończenie procesu w jego bieżącym stanie może spowodować niepożądane wyniki, w tym utratę danych i niestabilność systemu".

 Niezależnie od tego, czy w oknie dialogowym klikniesz przycisk **tak** , czy **nie** , program Visual Studio kończy proces programu Excel lub Word i zatrzymuje debuger. Aby zatrzymać debugowanie projektu bez wyświetlania tego okna dialogowego, należy natychmiast zamknąć program Excel lub Word, zamiast zatrzymywać debuger w programie Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Rozwiązywanie problemów z rozwiązaniami pakietu Office](../vsto/troubleshooting-office-solutions.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Rozwiązywanie problemów z wdrażaniem rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-deployment.md)
