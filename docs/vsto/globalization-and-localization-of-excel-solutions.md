---
title: Globalizacja i lokalizacja rozwiązania programu Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4a305a74d24b8480732fb2132bf6c25f4f4f3d7a
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647782"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalizacja i lokalizacja rozwiązania programu Excel
  Ta sekcja zawiera informacje o specjalne uwagi dotyczące rozwiązania Microsoft Office Excel, które będą uruchamiane na komputerach, które mają ustawienia innej niż angielska dla Windows. Większością aspektów globalizacja i lokalizacja pakietu Microsoft Office jest taki sam, Ci zaznajomić się podczas tworzenia innych rodzajów rozwiązań przy użyciu programu Visual Studio. Aby uzyskać ogólne informacje, zobacz [Globalize i lokalizacja aplikacji](/visualstudio/ide/globalizing-and-localizing-applications).  
  
 Domyślnie kontrolki hosta w programie Microsoft Office Excel pracach poprawnie w wszystkie ustawienia regionalne Windows tak długo, jak wszystkie dane, które są przekazywane lub modyfikować za pomocą kodu zarządzanego jest formatowana przy użyciu formatowania języka angielskiego (Stany Zjednoczone). W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], to zachowanie jest kontrolowany przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="format-data-in-excel-with-various-regional-settings"></a>Formatowanie danych w programie Excel za pomocą różnych ustawień regionalnych  
 Należy sformatować wszystkie dane, które jest zależne od ustawień regionalnych formatowania, takie jak daty i waluty, używając formatu danych angielski (Stany Zjednoczone) (locale ID 1033) przed przekazać go do programu Microsoft Office Excel lub odczytać danych z kodu w Office project.  
  
 Domyślnie podczas opracowywania rozwiązań pakietu Office w Visual Studio, model obiektów programu Excel oczekuje, że formatowanie danych 1033 identyfikator ustawień regionalnych (jest to również nazywane blokowania modelu obiektów 1033 identyfikator ustawień regionalnych). To zachowanie jest zgodne sposób działania Visual Basic for Applications. Jednak to zachowanie można zmienić w rozwiązaniach pakietu Office.  
  
### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Zrozumienie, jak model obiektów programu Excel zawsze oczekuje 1033 identyfikator ustawień regionalnych  
 Domyślnie rozwiązań pakietu Office, które tworzysz przy użyciu programu Visual Studio są niezależne od ustawień regionalnych użytkownika końcowego i zawsze zachowują się tak, jakby ustawienia regionalne jest angielski (Stany Zjednoczone). Na przykład, jeśli pobierania lub ustawiania <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> właściwości w programie Excel, dane muszą być sformatowane w sposób, który oczekuje, że identyfikator ustawień regionalnych 1033. Jeśli używasz formatu różnych danych, możesz otrzymać nieoczekiwane wyniki.  
  
 Mimo, że używasz formatu angielski (Stany Zjednoczone) dla danych, które są przekazywane lub zmieniane przez kod zarządzany, program Excel interpretuje i wyświetla dane prawidłowo zgodnie z ustawień regionalnych użytkownika końcowego. Excel można prawidłowo sformatować dane ponieważ kodu zarządzanego przekazuje format 1033 identyfikator ustawień regionalnych wraz z danymi, co oznacza, że dane są w języku angielskim (Stany Zjednoczone) i dlatego musi być ponownie sformatowany do dopasowania ustawień regionalnych użytkownika.  
  
 Na przykład jeśli użytkownicy końcowi mają swoich Opcje regionalne ustawienia regionalne niemiecki (Niemcy), spełniają oczekiwane data 29 czerwca 2005 r. do sformatowania w ten sposób: 29.06.2005. Jednak rozwiązanie przekazuje daty do programu Excel jako ciąg znaków, należy sformatować datę zgodnie z formatem języka angielskiego (Stany Zjednoczone): 6/29/2005. Komórka jest w formacie komórka typu Data, programu Excel wyświetli datę w formacie niemiecki (Niemcy).  
  
### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Przekaż inne identyfikatory ustawień regionalnych do modelu obiektów programu Excel  
 Środowisko uruchomieniowe języka wspólnego (CLR) przekazuje automatycznie 1033 identyfikator ustawień regionalnych dla wszystkich metod i właściwości w modelu obiektów programu Excel, które akceptują dane zależne od ustawień regionalnych. Nie istnieje żaden sposób, aby zmienić to zachowanie, automatycznie dla wszystkich wywołań modelu obiektów. Jednak można przekazać identyfikator innych ustawień regionalnych do określonej metody przy użyciu <xref:System.Type.InvokeMember%2A> do wywoływania metody i przekazując identyfikator ustawień regionalnych *kultury* parametru metody.  
  
## <a name="localize-document-text"></a>Lokalizowanie tekstu dokumentu  
 Dokument, szablonu lub skoroszytu w projekcie prawdopodobnie zawiera tekst statyczny, który musi być zlokalizowany oddzielnie z zestawu i inne zasoby zarządzane. Prostym sposobem na to jest kopię dokumentu i tłumaczenie tekstu za pomocą programu Microsoft Office Word lub Microsoft Office Excel. Ten proces działa nawet wtedy, gdy żadnych zmian w kodzie, ponieważ dowolną liczbę dokumenty mogą być połączone z tym samym zestawie.  
  
 Nadal należy się upewnić, że dowolną część swój kod, który wchodzi w interakcję z tekstu dokumentu w dalszym ciągu jest zgodny z językiem tekstu i tej zakładki nazwane zakresy, i innych pól wyświetlania pomieścić formatowania dokumentu pakietu Office, które było konieczne Dopasuj do innej długości gramatyki i tekst. Dla szablonów dokumentów, które zawierają stosunkowo mały tekst warto rozważyć przechowywanie tekstu w plikach zasobów, a następnie ładowania tekstu w czasie wykonywania.  
  
### <a name="text-direction"></a>Kierunek tekstu  
 W programie Excel można ustawić właściwości arkusza do renderowania tekstu od prawej do lewej. Hostowanie kontrolki lub dowolną kontrolkę, która ma `RightToLeft` właściwości, które jest umieszczone w Projektancie automatycznie odpowiadać następującym ustawieniom w czasie wykonywania. Word nie ma ustawienie dokumentu tekstu dwukierunkowego (po prostu Zmień swoje wyrównanie tekstu), więc kontrolki nie mogą być mapowane do tego ustawienia. Zamiast tego należy ustawić wyrównanie tekstu dla każdego formantu. Istnieje możliwość pisania kodu w celu zaprezentowania wszystkich kontrolek i wymusić renderowanie tekstu od prawej do lewej.  
  
### <a name="change-culture"></a>Zmienić kulturę  
 Dostosowania na poziomie dokumentu kod zazwyczaj udostępnia głównego wątku interfejsu użytkownika programu Excel, więc wszelkie zmiany wprowadzone w kultury wątku wpływa na wszystkie inne elementy, który działa na tym wątku; zmiany nie są ograniczone do dostosowanie.  
  
 Kontrolek formularzy Windows Forms są inicjowane przed VSTO application-level Add-ins są uruchamiane przez aplikację hosta. W takich sytuacjach należy zmienić kulturę przed ustawieniem kontrolek interfejsu użytkownika.  
  
## <a name="install-the-language-packs"></a>Zainstaluj pakiety językowe  
 W przypadku ustawienia innej niż angielska dla Windows można zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pakietów językowych, aby zobaczyć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wiadomości w języku Windows. Jeśli użytkowników uruchom swoje rozwiązania z ustawieniami innej niż angielska dla Windows, muszą one mieć pakiet językowy poprawna, aby wyświetlić komunikaty czasu wykonywania, w tym samym języku co Windows. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Pakiety językowe są dostępne z [Centrum pobierania Microsoft](http://www.microsoft.com/downloads).  
  
 Ponadto pakiet redystrybucyjny pakiety językowe programu .NET Framework są niezbędne dla wiadomości ClickOnce. Pakiety językowe programu .NET Framework są dostępne z [Centrum pobierania Microsoft](http://www.microsoft.com/downloads).  
  
## <a name="regional-settings-and-excel-com-calls"></a>Ustawienia regionalne i wywołania COM programu Excel  
 Zawsze, gdy klient zarządzany wywołuje metodę dla obiektów COM i potrzebny do przekazywania informacji specyficznych dla kultury, tak więc przy użyciu <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (ustawienia regionalne), które odpowiadają ustawień regionalnych bieżącego wątku. Bieżące ustawienia regionalne wątku są dziedziczone z ustawień regionalnych użytkownika w domyślnie. Jednak po wprowadzeniu wywołać model obiektów programu Excel z rozwiązania programu Excel utworzony przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, formatu danych angielski (Stany Zjednoczone) (locale ID 1033) jest przekazywany do modelu obiektów programu Excel automatycznie. Wszystkie dane, które jest zależne od ustawień regionalnych formatowania, takich jak daty i waluty, należy sformatować przy użyciu formatu danych angielski (Stany Zjednoczone), zanim przekazać go do programu Microsoft Office Excel lub odczytać danych z kodu projektu.  
  
## <a name="considerations-for-storing-data"></a>Uwagi dotyczące przechowywania danych  
 Aby upewnić się, że dane są poprawnie interpretowany i wyświetlany, należy również rozważyć, czy mogą wystąpić problemy, gdy aplikacja zapisuje dane, takie jak formuły w arkuszu programu Excel, w literałach ciągu (zakodowane) zamiast w silnie typizowanych obiektów. Należy użyć dane sformatowane przy założeniu stylu niezmiennej kulturze lub języku angielskim (Stany Zjednoczone) (LCID wartość 1033).  
  
### <a name="applications-that-use-string-literals"></a>Aplikacje, które używają literałów ciągów  
 Możliwe wartości, które mogą być zakodowane obejmują literały daty, które są zapisywane w formacie języka angielskiego (Stany Zjednoczone) i formuły arkusza programu Excel, które zawierają zlokalizowane nazwy. Inna możliwość może być ciągu ustalonych, który zawiera numer, takie jak "1000"; w niektórych kultur to jest interpretowane jako tysiąc, ale w innych kultur stanowi jeden punkt zero. Obliczeń i porównywanie wykonywane na nieprawidłowy format może spowodować nieprawidłowe dane.  
  
 Program Excel interpretuje wszystkie ciągi zgodnie z LCID, który jest przekazywany z ciągu. Może to być problemem, jeśli format ciągu nie odpowiada identyfikator LCID, który jest przekazywany. Rozwiązania programu Excel utworzony przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio Użyj 1033 LCID (en US), podczas przekazywania wszystkich danych. Powoduje wyświetlenie danych zgodnie z ustawieniami regionalnymi i język interfejsu użytkownika programu Excel. Visual Basic for Applications (VBA) działa również w ten sposób; ciągi są sformatowane jako en US i VBA prawie zawsze przekazuje 0 (niezależne od języka) jako identyfikator LCID. Na przykład poniższy kod VBA wyświetla prawidłowo sformatowaną wartość dla May 12, 2004, zgodnie z bieżących ustawień regionalnych użytkownika:  
  
```vb
'VBA  
Application.ActiveCell.Value2 = "05/12/04"  
```  
  
 Ten sam kod, gdy jest używana w ramach rozwiązania utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio i przekazywana do programu Excel Usługa międzyoperacyjna modelu COM, daje takie same wyniki podczas formatowania daty w stylu en US.  
  
 Na przykład:  
  
 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]  
  
 Powinien współpracować z silnie typizowanych danych zamiast literałów ciągów, jeśli to możliwe. Na przykład zamiast przechowywania daty w literale ciągu, zapisz go jako <xref:System.Double>, następnie przekonwertować go na <xref:System.DateTime> obiekt do manipulowania.  
  
 Poniższy przykładowy kod pobiera daty, który użytkownik wprowadza w komórce A5, przechowuje go w formie <xref:System.Double>, następnie konwertuje ją na <xref:System.DateTime> obiektu do wyświetlenia w komórce A7. Komórka A7 muszą być sformatowane do wyświetlania datę.  
  
 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]  
  
### <a name="excel-worksheet-functions"></a>Funkcje arkusza programu Excel  
 Nazwy funkcji w arkuszu są tłumaczone wewnętrznie dla większości wersji językowych programu Excel. Jednak ze względu na potencjalne języka i problemy międzyoperacyjne COM zaleca się używanie nazwy funkcji tylko w języku angielskim w kodzie.  
  
### <a name="applications-that-use-external-data"></a>Aplikacje korzystające z danych zewnętrznych  
 Wszelki kod, który zostanie otwarty lub w przeciwnym razie używa danych zewnętrznych, takich jak pliki, które zawierają wartości rozdzielanych przecinkami (CSV files) wyeksportowany ze starszego systemu może mieć wpływ również, jeśli takie pliki są eksportowane formacie oprócz en US. Dostęp do bazy danych nie może być wpływu, ponieważ wszystkie wartości powinny być w formacie binarnym, chyba że baza danych przechowuje daty w postaci ciągów lub wykonuje operacje, które nie korzystają z formatu binarnego. Ponadto można utworzyć zapytań SQL za pomocą danych z programu Excel, konieczne może być upewnij się, że są one w formacie en US, w zależności od funkcji, której używasz.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Docelowy urząd wielojęzyczny interfejs użytkownika](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  