---
title: Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 82f1d66b1d4159ddb7a2fc4526af65d6cf3a6ec0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865206"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
  Mogą wystąpić problemy podczas wykonywania następujących zadań, podczas opracowywania rozwiązań pakietu Office w Visual Studio:  
  
-   [Tworzenie, uaktualniania i otwierania projektów](#creating)  
  
-   [Używanie projektantów](#designers)  
  
-   [Pisanie kodu](#code)  
  
-   [Kompilowanie projektów](#building)  
  
-   [Debugowanie projektów](#debugging)  
  
##  <a name="creating"></a> Tworzenie, uaktualniania i otwierania projektów  
 Podczas tworzenia lub otwierania projektów pakietu Office, mogą wystąpić następujące błędy.  
  
### <a name="the-project-cannot-be-created"></a>Nie można utworzyć projektu  
 Wystąpił błąd podczas próby tworzenia lub otwierania projektu pakietu Office, ale Visual Studio nie ma wystarczających informacji, aby ustalić przyczynę. Zamknij projekt zamykania programu Visual Studio, a następnie ponownie uruchomić.  
  
 Jeśli próbujesz utworzyć projektu na poziomie dokumentu, istnieje możliwość, że innego dokumentu o takiej samej nazwie jako dokument w nowym projekcie jest już otwarty w programie Excel lub Word. Upewnij się, że wszystkie wystąpienia programu Excel lub Word są zamknięte.  
  
### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Właściwości kontrolek zostaną utracone podczas tworzenia nowego projektu na podstawie dokumentu z istniejącego projektu.  
 Jeśli tworzysz nowy projekt na podstawie dokumentu z istniejącego projektu, właściwości dla wszystkich formantów, które znajdują się w dokumencie nie są kopiowane do nowego projektu. Można ręcznie zresetować właściwości dla wszystkich istniejących formantów. Alternatywnie można zachować właściwości formantu, tworząc kopię istniejącego projektu zamiast tworzenia nowego projektu lub przez ładowanie istniejący projekt do nowego rozwiązania (w Projektancie) i kopiowanie i wklejanie kontrolki z istniejącego dokument do nowego dokumentu.  
  
### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Błędy podczas tworzenia projektu skoroszytu programu Excel, oparte na istniejący skoroszyt  
 Jeśli tworzysz nowy projekt skoroszytu programu Excel oparty na podstawie istniejącego skoroszytu, można napotkać kombinację następujących błędów.  
  
 Z poziomu programu Excel: "Ostrzeżenie dotyczące prywatności: Ten dokument zawiera makra, formanty ActiveX, informacje o pakietach rozszerzeń XML lub składniki sieci Web. Te mogą obejmować informacje osobiste, którego nie można usunąć przez inspektora dokumentu."  
  
 W programie Visual Studio: "Designer nie można prawidłowo załadować."  
  
 Te błędy mogą występować, spróbuj utworzyć projekt, który jest oparty na skoroszyt, który miał jego informacje osobiste, które zostały usunięte przy użyciu Inspektora dokumentu. Aby uniknąć tego błędu, należy wykonać poniższe kroki przed utworzeniem projektu.  
  
1.  Otwórz skoroszyt w programie Excel.  
  
2.  W programie Excel otwórz Centrum zaufania.  
  
3.  Na **opcje prywatności** kartę wyczyść **Usuń informacje osobiste z właściwości pliku przy zapisywaniu** pole wyboru.  
  
4.  Zapisz skoroszyt, a następnie zamknij program Excel.  
  
### <a name="cannot-open-a-project-after-migration"></a>Nie można otworzyć projektu po migracji  
 Po pakietu Office, które rozwiązanie jest migrowana do pakietu Microsoft Office 2010 nie można otworzyć projektu na komputerze deweloperskim z tylko systemu Microsoft Office 2007, które są zainstalowane. Mogą pojawić się następujące błędy.  
  
 "Jeden lub więcej projektów w rozwiązaniu nie zostały poprawnie załadowane. Zobacz okno danych wyjściowych, aby uzyskać szczegółowe informacje."  
  
 "Nie można utworzyć projektu, ponieważ aplikacja skojarzona z tym typem projektu nie jest zainstalowany na tym komputerze. Zainstalowanie aplikacji Microsoft Office, który jest skojarzony z tym typem projektu."  
  
 Aby rozwiązać ten problem, Edytuj *.vbproj* lub *.csproj* pliku. W projekcie programu Word Zastąp HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" z HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}". W projekcie programu Excel należy zastąpić HostPackage = "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" z HostPackage = "{825100CF-0BA7-47EA-A084-DCF3308DAF74}". W projekcie programu Outlook Zastąp HostPackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" z HostPackage = "{20A848B8-E01F-4801-962E-25DB0FF57389}".  
  
 Alternatywnie należy zapewnić, że zmigrowane projekty tylko są otwarte na komputerach rozwoju z już zainstalowany program Microsoft Office 2010.  
  
### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Błędy w uaktualnione projekty poziomu dokumentu pakietu Office 2003, zawierających formanty Windows Forms  
 Jeśli uaktualniasz projekt Microsoft Office 2003 poziomie dokumentu i dokument zawiera kontrolek formularzy Windows Forms, zaktualizowany projekt może być błędy kompilacji lub środowiska uruchomieniowego. Aby uniknąć tego problemu, zainstaluj program Visual Studio 2005 Tools for Office Second Edition Runtime na komputerze deweloperskim przed przystąpieniem do uaktualniania projektu. Ta wersja środowiska uruchomieniowego jest dostępna jako pakiet redystrybucyjny z Microsoft Download Center w [programu Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 Po zakończeniu uaktualniania projektu, można odinstalować Visual Studio 2005 Tools for Office Second Edition Runtime z komputera rozwoju Jeśli nie jest on używany przez inne rozwiązania pakietu Office.  
  
##  <a name="designers"></a> Używanie projektantów  
 Mogą wystąpić następujące błędy podczas pracy z dokumentu, skoroszytu lub arkusza projektanta w projektach na poziomie dokumentu.  
  
### <a name="designer-failed-to-load-correctly"></a>Nie można prawidłowo załadować projektanta  
 Program Visual Studio nie może otworzyć projektanta w następujących przypadkach:  
  
-   Word lub Excel jest już otwarty i wyświetla modalne okno dialogowe. Aby otworzyć projektanta, sprawdź, czy programu Excel lub Word ma modalne okno dialogowe Otwórz i zamknij wszystkie otwarte modalne okna dialogowe. Jeśli żadne modalne okna dialogowe są otwarte, mogą istnieć inne działania, wymagany dla programu Excel lub Word odpowiada.  
  
-   Projekt jest obecnie debugowane. Aby otworzyć projektanta, Zatrzymaj lub Zakończ debugowania.  
  
-   Dodatek narzędzi VSTO dla programu Excel zainstalowanym na komputerze deweloperskim jest wyświetlanie okna dialogowego po uruchomieniu programu Excel. Aby utworzyć projekt poziomu dokumentu programu Excel, należy najpierw wyłączyć dodatku narzędzi VSTO.  
  
### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Formanty są wyświetlane jako czarne prostokątów w dokumencie lub arkuszu  
 Jeśli grupowanie formantów na dokument lub skoroszyt programu Visual Studio nie rozpoznaje już kontrolki. Nie można uzyskać dostępu do kontrolki zgrupowane w **właściwości** okna i są wyświetlane jako czarne prostokątów w dokumencie lub arkuszu. Formanty musi rozgrupować w celu przywrócenia ich funkcjonalności.  
  
### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Formanty na szablon programu Word nie są widoczne w programie Visual Studio  
 Jeśli otworzysz szablon programu Word w Projektancie Visual Studio formantów na szablonie, które nie są zgodne z tekstu może nie być widoczne. Jest to spowodowane Visual Studio otwiera szablony programu Word w **normalny** widoku. Aby wyświetlić kontrolki, kliknij **widoku** menu wskaż **Microsoft Office Word widoku** a następnie kliknij przycisk **układ wydruku**.  
  
### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>INSERT clip art polecenia nie działa w Projektancie Visual Studio  
 Gdy programu Excel lub Word jest otwarty w Projektancie Visual Studio, klikając **clipart** znajdujący się na **ilustracje** nie można otworzyć kartę na wstążce **clipart** okienka zadań. Aby dodać obiekty clipart, należy otworzyć kopię skoroszytu lub dokument, który znajduje się w folderze głównym projektu (nie znajduje się w kopię *\bin* folder) poza programem Visual Studio Dodaj clipart, a następnie zapisz skoroszyt lub dokumentu.  
  
##  <a name="code"></a> Pisanie kodu  
 Podczas pisania kodu w projektach pakietu Office, mogą wystąpić następujące błędy.  
  
### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Niektóre zdarzenia obiektów pakietu Office nie są dostępne przy użyciu języka C#  
 W niektórych przypadkach można napotkać błąd kompilatora podobnie do następującego podczas próby dostępu do określonego zdarzenia wystąpienia w projektach Visual C# wpisz podstawowego zestawu międzyoperacyjnego (PIA) pakietu Office.  
  
 "Niejednoznaczności między"Microsoft.Office.Interop.Excel._Application.NewWorkbook"i"Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook""  
  
 Ten błąd oznacza, że próby dostępu do zdarzeń, który ma taką samą nazwę jak inny właściwości lub metody obiektu. Aby uzyskać dostęp do zdarzenia, należy rzutować obiekt do jego *interfejsu zdarzenia*.  
  
 Typy PIA pakietu Office, które mają zdarzenia implementuje dwa interfejsy: z interfejsu core za pomocą właściwości i metody i zdarzenia interfejsu, który zawiera zdarzenia, które są udostępniane przez obiekt. Te interfejsy zdarzeń Użyj konwencji nazewnictwa *objectname*zdarzenia*n*_zdarzenia, takich jak <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> i <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>. Jeśli nie masz dostępu do zdarzenia, które należy się spodziewać na obiekt, należy zrzutować obiektu do jego interfejsu zdarzenia.  
  
 Na przykład <xref:Microsoft.Office.Interop.Excel.Application> obiekty mają <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> zdarzeń i <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> właściwości. Do obsługi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> rzutowania zdarzenia <xref:Microsoft.Office.Interop.Excel.Application> do <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> interfejsu. Poniższy przykład kodu pokazuje, jak to zrobić w projekcie na poziomie dokumentu dla programu Excel.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]  
  
 Aby uzyskać więcej informacji na temat interfejsów zdarzeń w zestawy PIA pakietu Office, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](/previous-versions/office/office-12//ms247299(v=office.12)).  
  
### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>Nie można odwołania PIA pakietu Office klas w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], kod, który odwołuje się do klasy, która jest zdefiniowana w PIA pakietu Office nie zostanie skompilowany domyślnie. Klasy zestawów PIA używać konwencji nazewnictwa *objectname*klasy, takie jak <xref:Microsoft.Office.Interop.Word.DocumentClass> i <xref:Microsoft.Office.Interop.Excel.WorkbookClass>. Na przykład poniższy kod w projekcie dodatku narzędzi VSTO programu Word nie zostanie skompilowany.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Ten kod powoduje zwrócenie następujących błędów kompilacji:  
  
- Visual Basic: "Odwołania do klasy"Klasa dokumentu"jest niedozwolone podczas jej zestawu jest połączony, przy użyciu trybu nie-PIA."  
  
- Wizualne C#: "Typu międzyoperacyjnego, który nie może zostać osadzony"Microsoft.Office.Interop.Word.DocumentClass". Użyj odpowiedniego interfejsu."  
  
  Aby rozwiązać ten problem, należy zmodyfikować kod, aby odwołać zamiast tego odpowiedniego interfejsu. Na przykład, zamiast odwołania <xref:Microsoft.Office.Interop.Word.DocumentClass> obiekt; odwoływać się do wystąpienia <xref:Microsoft.Office.Interop.Word.Document> zamiast tego interfejsu.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Projekty przeznaczone [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], automatycznie osadzić wszystkich typów międzyoperacyjnych z zestawy PIA pakietu Office, domyślnie. Ten błąd kompilacji występuje, ponieważ funkcja osadzone typy międzyoperacyjne działa tylko z interfejsów, a nie z klas. Aby uzyskać więcej informacji dotyczących interfejsów i klas w zestawy PIA pakietu Office, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592). Aby uzyskać więcej informacji na temat funkcji osadzone typy międzyoperacyjne w projektach pakietu Office, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="references-to-office-classes-are-not-recognized"></a>Odwołania do klasy pakietu Office nie są rozpoznawane.  
 Niektóre nazwy klasy, na przykład aplikacja, znajdują się w wiele przestrzeni nazw takich jak <xref:Microsoft.Office.Interop.Word> i <xref:System.Windows.Forms>. Z tego powodu **Importy**/**przy użyciu** instrukcji w górnej części szablonów projektu zawiera skróconą formą kwalifikujących się stałą, na przykład:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]  
  
 To użycie **Importy**/**przy użyciu** instrukcja wymaga rozróżnienia odwołania do klasy pakietu Office z kwalifikatorem programu Word lub Excel, na przykład:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]  
  
 Zostanie wyświetlony błędy, jeśli na przykład użyć deklaracji niekwalifikowanych:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]  
  
 Nawet jeśli została zaimportowana z programu Word lub Excel przestrzeni nazw i mieć dostęp do wszystkich klas znajdującym się w nim, musi pełnej kwalifikacji wszystkich typów za pomocą programu Word lub Excel, aby usunąć niejednoznaczność przestrzeni nazw.  
  
##  <a name="building"></a> Kompilowanie projektów  
 Mogą wystąpić następujące błędy podczas kompilowania projektów pakietu Office.  
  
### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Nie można skompilować projektu poziomie dokumentu, który jest oparty na dokumentów z ograniczonymi uprawnieniami  
 Program Visual Studio nie może zbudować projektów na poziomie dokumentu, jeśli dokument ma ograniczone uprawnienia. Jeśli projekt zawiera dokument, który ma ograniczone uprawnienia, nie można skompilować projekt i zostanie wyświetlony następujący komunikat w **lista błędów** okna.  
  
 "Nie można dodać dostosowania".  
  
 Jeśli chcesz dołączyć dokument, który ma ograniczone uprawnienia, należy użyć dokumentu bez ograniczeń podczas rozwijania i budowania rozwiązania. Następnie Zastosuj ograniczone uprawnienia do dokumentu w lokalizacji publikowania, po opublikowaniu rozwiązania.  
  
### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Błędy kompilatora występują po usunięciu kontrolki NamedRange  
 Jeśli usuniesz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w arkuszu, który nie jest aktywny arkusz w Projektancie automatycznie wygenerowany kod nie może zostać usunięta z projektu i mogą wystąpić błędy kompilatora. Aby upewnić się, że kod zostanie usunięty, należy zawsze wybrać arkusz, który zawiera <xref:Microsoft.Office.Tools.Excel.NamedRange> celu nadania mu aktywnego arkusza przed usunięciem formantu. Automatycznie wygenerowany kod nie zostanie usunięta po usunięciu kontrolki, może spowodować projektanta Aby usunąć kod aktywacji arkusza i wprowadzenie zmiany, tak aby arkusz zostanie oznaczona jako zmodyfikowana. Podczas ponownego kompilowania projektu kodu jest usuwany.  
  
##  <a name="debugging"></a> Debugowanie projektów  
 Podczas debugowania w projektach pakietu Office, mogą wystąpić następujące błędy.  
  
### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Podczas publikowania i zainstalowanie rozwiązania na komputerze programisty, zostanie wyświetlony monit, aby odinstalować  
 Podczas debugowania rozwiązania do pakietu Office, może zostać wyświetlony następujący błąd.  
  
 "Nie można zainstalować dostosowania, ponieważ inna wersja jest obecnie zainstalowany i nie można uaktualnić z tej lokalizacji."  
  
 Ten błąd wskazuje, że został wcześniej opublikowana i zainstalowana rozwiązania dla pakietu Office na komputerze deweloperskim. Aby zapobiec pojawianiu się komunikat, należy odinstalować rozwiązania z listy zainstalowanych programów na komputerze zanim debugować rozwiązania. Alternatywnie można utworzyć innego konta użytkownika na komputerze dewelopera w celu przetestowania instalacji opublikowane rozwiązania.  
  
### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projektów na poziomie dokumentu utworzone w lokalizacjach sieciowych UNC nie należy uruchamiać z poziomu programu Visual Studio  
 Jeśli tworzysz projekt na poziomie dokumentu dla programu Excel lub Word w lokalizacji sieciowej UNC, należy dodać lokalizację dokumentu do listy zaufanych lokalizacji w programie Excel lub Word. W przeciwnym razie dostosowanie nie zostanie załadowany, podczas uruchamiania lub debugowania projektu w programie Visual Studio. Aby uzyskać więcej informacji na temat zaufanych lokalizacji, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Wątki nie są poprawnie zatrzymana po debugowaniu  
 Projekty pakietu Office w Visual Studio postępuj zgodnie z wątku konwencje, które umożliwiają debugerowi poprawnie zamknąć program nazewnictwa. Jeśli tworzysz wątków w rozwiązaniu, należy nadać nazwę każdego wątku z prefiksem VSTA_, aby upewnić się, że te wątki są obsługiwane poprawnie po zatrzymaniu debugowania. Na przykład możesz ustawić `Name` właściwość wątek, który oczekuje na zdarzenia sieci **VSTA_NetworkListener**.  
  
### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Nie można uruchomić lub debugować żadnych rozwiązań pakietu Office na komputerze deweloperskim  
 Jeśli nie można uruchomić lub tworzenia projektu pakietu Office na komputerze deweloperskim, zobaczysz następujący komunikat o błędzie.  
  
 "Dostosowania nie można załadować, ponieważ nie można utworzyć domeny aplikacji."  
  
 Visual Studio używa Fusion, moduł ładujący zestawu .NET Framework w pamięci podręcznej zestawów, przed załadowaniem rozwiązań pakietu Office. Upewnij się, że Visual Studio można zapisywanie w pamięci podręcznej łączenia i spróbuj ponownie. Aby uzyskać więcej informacji, zobacz [zestawów kopii w tle](/dotnet/framework/app-domains/shadow-copy-assemblies).  
  
### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Błąd podczas zatrzymywania debugera w projekcie na poziomie dokumentu po użyciu Edytuj i Kontynuuj  
 Jeśli używasz **Edytuj** i **Kontynuuj** Aby wprowadzić zmiany do kodu w projekcie na poziomie dokumentu dla programu Excel lub Word, podczas gdy projekt jest w trybie przerwania, może być wyświetlone okno dialogowe, za pomocą następujący komunikat o błędzie, jeśli użytkownik następnie Przerwij debugowanie.  
  
 "Zakończenie procesu w jego bieżącym stanie może spowodować niepożądane skutki, w tym utratę danych i niestabilność systemu."  
  
 Czy możesz kliknąć pozycję **tak** lub **nie** w oknie dialogowym programu Visual Studio kończy proces programu Excel lub Word i zatrzymuje się debuger. Aby zatrzymać debugowanie projektu bez wyświetlania tego okna dialogowego, Zakończ działanie programu Excel lub Word bezpośrednio zamiast zatrzymanie debugera w programie Visual Studio.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązywanie problemów z rozwiązań pakietu Office](../vsto/troubleshooting-office-solutions.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Rozwiązywanie problemów z wdrażaniem rozwiązań Office](../vsto/troubleshooting-office-solution-deployment.md)  
