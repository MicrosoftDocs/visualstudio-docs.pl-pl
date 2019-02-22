---
title: Łączenie VBA i dostosowywanie na poziomie dokumentu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a0e944d2ed8538a72082bdc52ee72058907ed9d5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633281"
---
# <a name="combine-vba-and-document-level-customizations"></a>Łączenie VBA i dostosowywanie na poziomie dokumentu
  Za pomocą języka Visual Basic for Applications (VBA) kodu w dokumencie, który jest częścią dostosowywania poziomie dokumentu dla programu Microsoft Office Word lub Microsoft Office Excel. Możesz wywołać kod VBA w dokumencie z zestawu dostosowywania lub projektu w celu włączenia kodu z VBA w dokumencie w celu wywołania kodu w zestaw dostosowania można skonfigurować.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Zachowanie kodu z VBA w dostosowaniu na poziomie dokumentu
 Po otwarciu projektu w programie Visual Studio, dokument jest otwarty w trybie projektowania. Kod VBA nie jest uruchamiany, gdy dokument jest w trybie projektowania, aby można było pracować w dokumencie i kodu bez uruchamiania kodu VBA.

 Po uruchomieniu rozwiązania, procedury obsługi zdarzeń w VBA i zestaw dostosowania wybierz zdarzenia, które są wywoływane w dokumencie, a następnie uruchom oba zestawy kodu. Nie można ustalić wcześniej kod, który będzie wykonywany przed innymi; należy to określić za pomocą testowania w każdym przypadku. Jeśli nie dokładnie koordynowany i testowane dwa rodzaje kodu, możesz uzyskać nieoczekiwane wyniki.

## <a name="call-vba-code-from-the-customization-assembly"></a>Wywoływanie kodu z VBA z zestaw dostosowania
 Makra można wywołać w dokumentach programu Word i może wywołać makra i funkcje, które znajdują się w skoroszytach programu Excel. Aby to zrobić, użyj jednej z następujących metod:

- Dla programu Word, należy wywołać <xref:Microsoft.Office.Interop.Word._Application.Run%2A>metody <xref:Microsoft.Office.Interop.Word.Application> klasy.

- Dla programu Excel, należy wywołać <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> metody <xref:Microsoft.Office.Interop.Excel.Application> klasy.

  Dla każdej metody pierwszy parametr określa nazwę makro lub funkcja, którą chcesz się połączyć, a pozostałe parametry opcjonalne parametry do przekazania do makro lub funkcja. Pierwszy parametr może mieć różne formaty dla programów Word i Excel:

- Dla programu Word pierwszy parametr jest ciąg, który może być dowolną kombinacją szablonu, modułu i nazwą makra. Jeśli określisz nazwę dokumentu, kod można uruchamiać tylko makra w dokumentach związane z bieżącego kontekstu — nie do byle makra w każdym dokumencie.

- Dla programu Excel, pierwszy parametr może być ciąg, który określa nazwę makra <xref:Microsoft.Office.Interop.Excel.Range> oznacza to, gdzie jest funkcja lub identyfikator rejestru w zarejestrowanej funkcji DLL (XLL). Jeśli przekażesz ciąg, ciąg zostanie ocenione w ramach aktywnego arkusza.

  Poniższy przykład kodu pokazuje sposób wywołania makra o nazwie `MyMacro` z projektu poziomie dokumentu dla programu Excel. W tym przykładzie założono, że `MyMacro` jest zdefiniowany w `Sheet1`.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
>  Aby uzyskać informacje o korzystaniu z globalnych `missing` zmiennej zamiast następujące parametry opcjonalne w Visual C#, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Wywoływanie kodu w dostosowaniach na poziomie dokumentu z kodu VBA
 Można skonfigurować projektem na poziomie dokumentu dla programu Word lub Excel, tak że kod Visual Basic for Applications (VBA) w dokumencie może wywoływać kod w zestawie dostosowywania. Jest to przydatne w następujących scenariuszach:

- Chcesz rozszerzyć istniejący kod VBA w dokumencie, korzystając z funkcji dostosowywania poziomie dokumentu, który jest skojarzony z tym samym dokumencie.

- Chcesz udostępnić usług, które rozwijasz w dostosowaniu na poziomie dokumentu użytkownicy końcowi, którzy mogą uzyskiwać dostęp przez napisanie kodu VBA w dokumencie usługi.

  Narzędzi programistycznych pakietu Office w programie Visual Studio udostępniają podobne funkcji dla dodatków narzędzi VSTO. Tworzenia dodatku narzędzi VSTO możesz wywołać kodu w dodatku VSTO z innych rozwiązań programu Microsoft Office. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
>  Nie można użyć tej funkcji w projektach szablon programu Word. Może służyć tylko w dokumencie programu Word, skoroszyt programu Excel lub projekty szablonu programu Excel.

## <a name="requirements"></a>Wymagania
 Przed włączeniem kodu VBA w celu wywołania do zestawu dostosowywania projektu muszą spełniać następujące wymagania:

-   Dokument musi mieć jedną z następujących rozszerzeń nazw plików:

    -   Dla programu Word: *.docm* lub *.doc*

    -   Dla programu Excel: *.xlsm*, *xltm*, *xls*, lub *.xlt*

-   Dokument już musi zawierać projekt VBA, który zawiera kod VBA.

-   Kod VBA w dokumencie musi mieć możliwość uruchamiania bez monitowania użytkownika o włączenie makr. Kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel można ufać.

-   Projekt pakietu Office musi zawierać co najmniej jeden Klasa publiczna, która zawiera co najmniej jeden publiczne elementy członkowskie, które wyświetlasz VBA.

     Może narazić metody, właściwości i zdarzeń z VBA. Klasy, który należy udostępnić może być klasą elementu hosta (takie jak `ThisDocument` dla programu Word, lub `ThisWorkbook` i `Sheet1` dla programu Excel) lub innej klasy, który zdefiniujesz w projekcie. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Włącz kod VBA do wywołania w zestawie dostosowywania
 Istnieją dwa różne sposoby, udostępnić elementów członkowskich w zestawie dostosowania dla kodu VBA w dokumencie:

- Można udostępnić składowe klasy elementu hosta w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu VBA. Aby to zrobić, należy ustawić **EnableVbaCallers** właściwości elementu hosta do **True** w **właściwości** okno podczas element hosta (oznacza to, dokument, arkuszu lub skoroszycie) Otwórz w projektancie. Program Visual Studio automatycznie wykonuje wszystkie zadania wymagane do włączenia kodu VBA wywołać składowe klasy.

- Można udostępnić elementów członkowskich w dowolnej klasy publicznej w projektach Visual C# lub elementy członkowskie w innych hostów elementu klasy w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu VBA. Ta opcja zapewnia większą swobodę wyboru klas, które należy udostępnić VBA, ale wymaga to również więcej czynności ręcznych.

   Aby to zrobić, należy wykonać następujące podstawowe kroki:

  1.  Udostępnianie klas dla modelu COM.

  2.  Zastąp **GetAutomationObject** metody klasy elementu hosta w projekcie, aby zwrócić wystąpienia klasy, które wyświetlasz VBA.

  3.  Ustaw **ReferenceAssemblyFromVbaProject** właściwości każdej klasy elementu hosta w projekcie, aby **True**. To zestaw dostosowania biblioteki typów są osadzone w zestawie i dodaje odwołanie do biblioteki typów do projektu VBA w dokumencie.

  Aby uzyskać szczegółowe instrukcje, zobacz [jak: Udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) i [jak: Udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

  **EnableVbaCallers** i **ReferenceAssemblyFromVbaProject** właściwości są dostępne tylko w **właściwości** okna w czasie projektowania; nie można używać w czasie wykonywania . Aby wyświetlić właściwości, otwórz projektanta dla elementu hosta w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji na temat konkretnych zadań wykonywanych w programie Visual Studio do ustawiania tych właściwości, zobacz [zadania wykonywane przez hosta właściwości elementu](#PropertyTasks).

> [!NOTE]
>  Jeśli skoroszyt lub dokument nie zawiera kodu VBA, lub jeżeli kod VBA w dokumencie nie jest zaufane do uruchamiania, otrzymasz komunikat o błędzie, gdy ustawisz **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject**  właściwości **True**. Jest to spowodowane programu Visual Studio nie można modyfikować projektu VBA w dokumencie w takiej sytuacji.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>W kod VBA używać elementów członkowskich do wywołania w zestawie dostosowywania
 Po skonfigurowaniu projektu w celu włączenia kodu VBA w celu wywołania do dostosowywania zestawu Visual Studio dodaje następujące elementy członkowskie do projektu VBA w dokumencie:

- Dla wszystkich projektów programu Visual Studio dodaje globalny metodę o nazwie `GetManagedClass`.

- Dla [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] klasa elementu projektów, w których elementy członkowskie hosta, należy udostępnić za pomocą **EnableVbaCallers** właściwości program Visual Studio dodaje również właściwość o nazwie `CallVSTOAssembly` do `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, lub `Sheet3` modułu w projekcie języka VBA.

  Możesz użyć `CallVSTOAssembly` właściwości lub `GetManagedClass` metodę, aby dostęp do publicznych elementów członkowskich klasy, które są widoczne dla kodu VBA w projekcie.

> [!NOTE]
>  Podczas tworzenia i wdrażania rozwiązania istnieje kilka różnych kopii dokumentu, gdzie można dodać kod VBA. Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące dodawania VBA kodu w dokumencie](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Użyj właściwości CallVSTOAssembly w projekcie Visual Basic
 Użyj `CallVSTOAssembly` właściwości publiczne elementy członkowskie, które zostały dodane do klasy elementu hosta dostępu. Na przykład, Poniższe makro VBA wywołuje metodę o nazwie `MyVSTOMethod` zdefiniowanego w `Sheet1` klasy w projekcie skoroszytu programu Excel.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Ta właściwość jest wygodniejszy sposób wywołania zestaw dostosowania niż przy użyciu `GetManagedClass` bezpośrednio metodę. `CallVSTOAssembly` Zwraca obiekt, który reprezentuje hosta klasa elementu, która zostanie udostępniane VBA. Elementy członkowskie i parametry metod zwróconego obiektu są wyświetlane w IntelliSense.

 `CallVSTOAssembly` Właściwość ma deklaracji, która jest podobna do poniższego kodu. Ten kod zakłada, że są dostępne `Sheet1` hosta elementu klasy w projekcie skoroszytu programu Excel o nazwie `ExcelWorkbook1` VBA.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Użyj metody GetManagedClass
 Używać globalnego `GetManagedClass` metody, przekaż obiekt VBA, który odnosi się do klasy elementu hosta, która zawiera zastąpienie metody **GetAutomationObject** metody. Następnie użyj zwróconego obiektu dostępu do tej klasy, która widoczna VBA.

 Na przykład, Poniższe makro VBA wywołuje metodę o nazwie `MyVSTOMethod` zdefiniowanego w `Sheet1` hosta elementu klasy w projekcie skoroszytu programu Excel o nazwie `ExcelWorkbook1`.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 `GetManagedClass` Metoda ma następującą deklarację.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Ta metoda zwraca obiekt, który reprezentuje klasę, która zostanie udostępniane VBA. Elementy członkowskie i parametry metod zwróconego obiektu są wyświetlane w IntelliSense.

##  <a name="Guidelines"></a> Wytyczne dotyczące dodawania kodu z VBA w dokumencie
 Istnieje kilka różnych kopii dokumentu, gdzie można dodać kod VBA tworzy wywołania do dostosowywania poziomie dokumentu.

 Podczas tworzenia i testowania rozwiązania, można napisać kod VBA w dokumencie, który zostanie otwarty podczas debugowania lub uruchomić projekt w programie Visual Studio (oznacza to, że dokument w folderze wyjściowym kompilacji). Jednak kod VBA dodawany do tego dokumentu zostaną zastąpione przy następnym uruchomieniu kompilacji projektu, ponieważ program Visual Studio zastępuje dokument w folderze wyjściowym kompilacji kopię dokumentu z folderu głównego projektu.

 Jeśli chcesz zapisać ten kod, Dodaj do dokumentu podczas debugowania i uruchamiania rozwiązania, należy skopiować kod VBA do dokumentu w folderze projektu. Aby uzyskać więcej informacji na temat procesu kompilacji, zobacz [tworzenie rozwiązań pakietu office](../vsto/building-office-solutions.md).

 Gdy wszystko jest gotowe do wdrożenia rozwiązania, istnieją trzy lokalizacje dokumentu głównego, w których można dodać kod VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>W folderze projektu na komputerze deweloperskim
 Ta lokalizacja jest wygodne, jeśli masz pełną kontrolę nad zarówno kod VBA w dokumencie, jak i kod dostosowania. Ponieważ dokument jest na komputerze deweloperskim, można łatwo zmodyfikować kodu VBA, jeśli zmienisz kod dostosowania. Kod VBA dodać tę kopię dokumentu pozostaje w dokumencie, podczas tworzenia, debugowania i publikowania rozwiązania.

 Nie można dodać kod VBA w dokumencie, podczas gdy jest on otwarty w projektancie. Najpierw zamknąć dokument w projektancie, a następnie otwórz dokument bezpośrednio w programie Word lub Excel.

> [!CAUTION]
>  Jeśli dodasz kod VBA, który jest uruchamiany, gdy dokument jest otwarty, w rzadkich przypadkach ten kod może spowodować uszkodzenie dokumentu lub uniemożliwić jego otwieranie w projektancie.

### <a name="in-the-publish-or-installation-folder"></a>W folderze publikowania lub instalacji
 W niektórych przypadkach może być odpowiednie dla Dodaj kod VBA w dokumencie w folderze publikowania lub instalacji. Na przykład wybierz tę opcję, jeśli kod VBA jest zapisywane i przetestowane przez różnych deweloperów na komputerze, który nie ma zainstalowanego programu Visual Studio.

 Jeśli użytkownicy instalują rozwiązanie bezpośrednio z folderu publikowania, należy dodać kod VBA w dokumencie za każdym razem, gdy będziesz publikować rozwiązanie. Program Visual Studio zastępuje dokument w lokalizacji publikowania, gdy będziesz publikować rozwiązanie.

 Jeśli użytkownicy instalują rozwiązanie z folderu instalacyjnego, która różni się od folderu publikowania, można uniknąć, dodając kod VBA w dokumencie, za każdym razem, gdy będziesz publikować rozwiązanie. Podczas aktualizacji publikowania jest gotowa do przeniesienia z folderu publikowania do folderu instalacji, należy skopiować wszystkie pliki do folderu instalacji z wyjątkiem dokumentu.

### <a name="on-the-end-user-computer"></a>Na komputerze użytkownika końcowego
 Jeśli użytkownicy końcowi VBA deweloperów, którzy wywołania do usługi, które zapewniają w dostosowaniu na poziomie dokumentu, możesz przekazać im, jak wywoływać kod za pomocą `CallVSTOAssembly` właściwości lub `GetManagedClass` metody w swoich kopii dokumentu. Podczas publikowania aktualizacji rozwiązanie kodu z VBA w dokumencie na komputerze użytkownika końcowego nie zostaną zastąpione, ponieważ dokument nie jest modyfikowany przez publikowanie aktualizacji.

##  <a name="PropertyTasks"></a> Zadania wykonywane przez właściwości elementu hosta
 Kiedy używasz **EnableVbaCallers** i **ReferenceAssemblyFromVbaProject** właściwości, Visual Studio wykonuje różne zestawy zadań.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Po ustawieniu **EnableVbaCallers** właściwości elementu hosta do **True** w projekcie języka Visual Basic, Visual Studio wykonuje następujące zadania:

1. Dodaje <xref:Microsoft.VisualBasic.ComClassAttribute> i <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutów do klasy elementu host.

2. Zastępuje ona **GetAutomationObject** metody klasy elementu host.

3. Ustawia **ReferenceAssemblyFromVbaProject** właściwości elementu hosta do **True**.

   Po ustawieniu **EnableVbaCallers** właściwości z powrotem do **False**, Visual Studio wykonuje następujące zadania:

4. Usuwa <xref:Microsoft.VisualBasic.ComClassAttribute> i <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybuty z `ThisDocument` klasy.

5. Usuwa **GetAutomationObject** metody z klasy elementu host.

   > [!NOTE]
   >  Program Visual Studio automatycznie nie ustawiono **ReferenceAssemblyFromVbaProject** właściwości z powrotem do **False**. Można ustawić tę właściwość na **False** ręcznie przy użyciu **właściwości** okna.

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Gdy **ReferenceAssemblyFromVbaProject** elementu hosta w projekcie języka Visual Basic lub Visual C# jest właściwością **True**, Visual Studio wykonuje następujące zadania:

1. On generuje bibliotekę typów dla zestawu dostosowywania i osadza biblioteki typów w zestawie.

2. Dodaje odwołania do następujących bibliotek typów projektu VBA w dokumencie:

   -   Biblioteka typów dla zestawu dostosowywania.

   -   Microsoft Visual Studio Tools dla pakietu Office wykonanie aparatu 9.0 biblioteki typów. Ta biblioteka typów znajduje się w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

   Gdy **ReferenceAssemblyFromVbaProject** właściwość jest ustawiana dla **False**, Visual Studio wykonuje następujące zadania:

3. Powoduje usunięcie odwołań do biblioteki typów z projektu VBA w dokumencie.

4. Biblioteka typów osadzonych powoduje usunięcie z zestawu.

## <a name="troubleshoot"></a>Rozwiązywanie problemów
 W poniższej tabeli wymieniono niektóre typowe błędy i sugestie dotyczące poprawiania błędów.

|Błąd|Sugestia|
|-----------|----------------|
|Po ustawieniu **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** właściwości, komunikat o błędzie stwierdzający, że dokument nie zawiera projektu VBA lub nie masz uprawnień dostępu do Projektu VBA w dokumencie.|Upewnij się, dokument w projekcie zawiera co najmniej jedno makro VBA, projektu VBA relacją zaufania wystarczające, aby uruchomić i projektu VBA nie jest chroniony hasłem.|
|Po ustawieniu **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** właściwość, komunikat o błędzie stwierdza, że <xref:System.Runtime.InteropServices.GuidAttribute> deklaracji lub jest uszkodzony.|Upewnij się, że <xref:System.Runtime.InteropServices.GuidAttribute> deklaracja znajduje się w *AssemblyInfo.cs* lub *AssemblyInfo.vb* plik w projekcie i czy ten atrybut jest ustawiony na prawidłowy identyfikator GUID.|
|Po ustawieniu **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** właściwości, komunikat o błędzie stwierdzający, że numer wersji określony przez <xref:System.Reflection.AssemblyVersionAttribute> jest nieprawidłowy.|Upewnij się, że <xref:System.Reflection.AssemblyVersionAttribute> deklaracji w *AssemblyInfo.cs* lub *AssemblyInfo.vb* plik w projekcie jest ustawiona na prawidłowy zestaw numer wersji. Uzyskać informacji o numerach wersji prawidłowego zestawu, zobacz <xref:System.Reflection.AssemblyVersionAttribute> klasy.|
|Po zmianie nazwy zestawu dostosowywania kod VBA tworzy wywołania w zestawie dostosowywania przestanie działać.|Jeśli zmienisz nazwę zestawu dostosowywania po udostępnisz ją dla kodu VBA, łącza między projektu VBA w dokumencie i zestaw dostosowania zostanie przerwane. Aby rozwiązać ten problem, zmień **ReferenceFromVbaAssembly** właściwość w projekcie na **False** , a następnie ponownie do **True**, a następnie Zastąp wszystkie odwołania do starych zestawu Nazwa kodu z VBA w ramach nowej nazwy zestawu.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Instrukcje: Udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Przewodnik: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Rozwiązania VBA i pakietu Office w Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
