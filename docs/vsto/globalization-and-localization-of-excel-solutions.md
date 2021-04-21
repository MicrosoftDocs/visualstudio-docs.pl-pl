---
title: Globalizacja i lokalizacja rozwiązań programu Excel
description: Zapoznaj się ze specjalnymi zagadnieniami Microsoft Office programu Excel, które będą uruchamiane na komputerach z ustawieniami systemu Windows w wersji językowej innych niż angielska.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3d77085808fb54cd0a0517cc6d039e2345a1872
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827984"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalizacja i lokalizacja rozwiązań programu Excel
  Ta sekcja zawiera informacje dotyczące specjalnych kwestii dotyczących Microsoft Office programu Excel, które będą uruchamiane na komputerach z ustawieniami systemu Windows w wersji językowej innych niż angielska. Większość aspektów globalizacji i lokalizacji rozwiązań Microsoft Office są takie same jak podczas tworzenia innych rodzajów rozwiązań przy użyciu Visual Studio. Aby uzyskać ogólne informacje, zobacz [Globalizowanie i lokalizacja aplikacji.](../ide/globalizing-and-localizing-applications.md)

 Domyślnie kontrolki hosta w programie Microsoft Office Excel działają poprawnie w dowolnym ustawieniach regionalnych systemu Windows, o ile wszystkie dane przekazywane lub manipulowane przy użyciu kodu zarządzanego są formatowane przy użyciu formatowania w języku angielskim (Stany Zjednoczone). W projektach, które są ukierunkowane na element lub , to zachowanie jest kontrolowane przez środowisko uruchomieniowe [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] języka wspólnego (CLR).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Formatowanie danych w programie Excel przy użyciu różnych ustawień regionalnych
 Należy sformatować wszystkie dane z formatowaniem wrażliwym na ustawieniach regionalnych, takie jak daty i waluta, przy użyciu formatu danych w języku angielskim (Stany Zjednoczone) (identyfikator regionalny 1033), zanim przekażemy je do programu Microsoft Office Excel lub odczytasz dane z kodu w projekcie pakietu Office.

 Domyślnie podczas opracowywania rozwiązania pakietu Office w programie Visual Studio model obiektów programu Excel oczekuje formatowania danych o identyfikatorze ustawień regionalnych 1033 (jest to również nazywane blokowaniem modelu obiektów dla ustawień regionalnych o identyfikatorze 1033). To zachowanie pasuje do sposobu, w jaki Visual Basic for Applications działa. To zachowanie można jednak zmodyfikować w rozwiązaniach pakietu Office.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Dowiedz się, w jaki sposób model obiektów programu Excel zawsze oczekuje identyfikatorów regionalnych 1033
 Domyślnie ustawienia ustawień regionalnych użytkownika końcowego nie wpływają na rozwiązania pakietu Office, które tworzysz przy użyciu usługi Visual Studio, i zawsze zachowują się tak, jakby ustawienia lokalne były w języku angielskim (Stany Zjednoczone). Jeśli na przykład pobierzemy lub ustawisz właściwość w programie Excel, dane muszą być sformatowane w sposób, który oczekuje identyfikatora <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 1033 dla danych regionalnych. Jeśli używasz innego formatu danych, możesz uzyskać nieoczekiwane wyniki.

 Mimo że dla danych przekazywanych lub manipulowanych przez zarządzany kod jest używany format angielski (Stany Zjednoczone), program Excel interpretuje i wyświetla dane poprawnie zgodnie z ustawieniami regionalnymi użytkownika końcowego. Program Excel może poprawnie sformatować dane, ponieważ kod zarządzany przekazuje identyfikator ustawień regionalnych 1033 wraz z danymi, co oznacza, że dane są w formacie angielskim (Stany Zjednoczone) i dlatego muszą zostać ponownie sformatowane w celu dopasowania do ustawień regionalnych użytkownika.

 Jeśli na przykład użytkownicy końcowi mają opcje regionalne ustawione na niemieckie (Niemcy), oczekują, że data 29 czerwca 2005 r. zostanie sformatowana w ten sposób: 29.06.2005. Jeśli jednak rozwiązanie przekazuje datę do programu Excel jako ciąg, należy sformatować datę zgodnie z formatem angielski (Stany Zjednoczone): 29.06.2005. Jeśli komórka jest sformatowana jako komórka Date( Data), program Excel wyświetli datę w formacie niemieckim (Niemcy).

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Przekaż inne identyfikatory regionalnych do modelu obiektów programu Excel
 Środowisko uruchomieniowe języka wspólnego (CLR) automatycznie przekazuje ustawienia lokalne o identyfikatorze 1033 do wszystkich metod i właściwości w modelu obiektów programu Excel, które akceptują dane wrażliwe na ustawienia lokalne. Nie ma możliwości automatycznej zmiany tego zachowania dla wszystkich wywołań w modelu obiektów. Można jednak przekazać inny identyfikator ustawień regionalnych do określonej metody przy użyciu metody , aby wywołać metodę i przekazując identyfikator ustawień regionalnych do parametru <xref:System.Type.InvokeMember%2A> culture metody . 

## <a name="localize-document-text"></a>Localize document text (Lokalizacja tekstu dokumentu)
 Dokument, szablon lub skoroszyt w projekcie prawdopodobnie zawiera tekst statyczny, który musi być zlokalizowany niezależnie od zestawu i innych zarządzanych zasobów. W tym celu można w prosty sposób wykonać kopię dokumentu i przetłumaczyć tekst przy użyciu Microsoft Office Word lub Microsoft Office Excel. Ten proces działa, nawet jeśli nie wprowadzasz żadnych zmian w kodzie, ponieważ dowolna liczba dokumentów może być połączona z tym samym zestawem.

 Nadal musisz upewnić się, że dowolna część kodu, która wchodzi w interakcję z tekstem dokumentu, będzie nadal odpowiadać językowi tekstu, a zakładki, nazwane zakresy i inne pola wyświetlania będą uwzględniać wszelkie zmiany sformatowane dokumentu pakietu Office, które było niezbędne do dostosowania do różnych gramatyki i długości tekstu. W przypadku szablonów dokumentów, które zawierają stosunkowo mało tekstu, warto rozważyć zapisanie tekstu w plikach zasobów, a następnie załadowanie go w czasie uruchomienia.

### <a name="text-direction"></a>Kierunek tekstu
 W programie Excel można ustawić właściwość arkusza w celu renderowania tekstu od prawej do lewej. Kontrolki hosta lub dowolna kontrolka, która ma właściwość, która jest umieszczana w projektancie, automatycznie pasują `RightToLeft` do tych ustawień w czasie działania. Program Word nie ma ustawienia dokumentu dla tekstu dwukierunkowego (wystarczy zmienić wyrównanie tekstu), więc nie można mapować kontrolek na to ustawienie. Zamiast tego należy ustawić wyrównanie tekstu dla każdej kontrolki. Istnieje możliwość napisania kodu, który będzie przechodzić przez wszystkie kontrolki i wymuszać renderowanie tekstu od prawej do lewej.

### <a name="change-culture"></a>Zmiana kultury
 Kod dostosowywania na poziomie dokumentu zazwyczaj udostępnia główny wątek interfejsu użytkownika programu Excel, więc wszelkie zmiany wprowadzone w kulturze wątku mają wpływ na wszystkie inne elementy uruchomione w tym wątku. Zmiana nie jest ograniczona do dostosowania.

 Windows Forms są inicjowanie przed wprowadzeniem dodatków VSTO na poziomie aplikacji przez aplikację hosta. W takich sytuacjach należy zmienić kulturę przed ustawieniem kontrolek interfejsu użytkownika.

## <a name="install-the-language-packs"></a>Instalowanie pakietów językowych
 Jeśli masz ustawienia systemu Windows inne niż angielski, możesz zainstalować pakiety językowe, aby wyświetlić komunikaty [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] w tym samym języku co system Windows. Jeśli dowolny użytkownik końcowy uruchamia Twoje rozwiązania z ustawieniami systemu Windows w języku innym niż angielski, musi mieć odpowiedni pakiet językowy, aby wyświetlić komunikaty środowiska uruchomieniowego w tym samym języku co system Windows. Pakiety [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] językowe są dostępne w Centrum pobierania [Microsoft.](https://www.microsoft.com/download)

 Ponadto pakiety językowe pakietów .NET Framework są niezbędne dla komunikatów ClickOnce. Pakiety .NET Framework language pack są dostępne w [Centrum pobierania Firmy Microsoft.](https://www.microsoft.com/download)

## <a name="regional-settings-and-excel-com-calls"></a>Ustawienia regionalne i wywołania COM programu Excel
 Zawsze, gdy klient zarządzany wywołuje metodę w obiekcie COM i musi przekazać informacje specyficzne dla kultury, robi to przy użyciu (ustawieniach regionalnych), które są takie, które są zgodnie z bieżącymi ustawieniami regionalnymi <xref:System.Globalization.CultureInfo.CurrentCulture%2A> wątku. Bieżące ustawienia regionalne wątku są domyślnie dziedziczone z ustawień regionalnych użytkownika. Jednak po wywołaniu modelu obiektu programu Excel z rozwiązania programu Excel utworzonego przy użyciu narzędzi programistyki pakietu Office w programie Visual Studio format danych w języku angielskim (Stany Zjednoczone) (identyfikator regionalny 1033) jest automatycznie przekazywany do modelu obiektów programu Excel. Musisz sformatować wszystkie dane, które mają formatowanie z wykorzystaniem danych ważnych dla ustawieniach regionalnych, takie jak daty i waluta, używając formatu danych w języku angielskim (Stany Zjednoczone), zanim przekażemy je do programu Microsoft Office Excel lub odczytasz dane z kodu projektu.

## <a name="considerations-for-storing-data"></a>Zagadnienia dotyczące przechowywania danych
 Aby upewnić się, że dane są prawidłowo interpretowane i wyświetlane, należy również wziąć pod uwagę, że problemy mogą wystąpić, gdy aplikacja przechowuje dane, takie jak formuły arkusza programu Excel, w literałach ciągu (zakodowanych) zamiast w silnie typowanych obiektach. Należy używać danych sformatowanych przy założeniu niezmiennej kultury lub języka angielskiego (Stany Zjednoczone) (wartość LCID 1033).

### <a name="applications-that-use-string-literals"></a>Aplikacje, które używają literałów ciągów
 Możliwe wartości, które mogą być zakodowane na bieżąco, obejmują literały daty zapisane w formacie języka angielskiego (Stany Zjednoczone) i formuły arkusza programu Excel, które zawierają zlokalizowane nazwy funkcji. Inną możliwością może być zakodowany ciąg zawierający liczbę, taką jak "1000"; W niektórych kulturach jest to interpretowane jako tysiąc, ale w innych kulturach reprezentuje jeden punkt zero. Obliczenia i porównania wykonywane w niewłaściwym formacie mogą spowodować nieprawidłowe dane.

 Program Excel interpretuje wszelkie ciągi zgodnie z wartością LCID przekazywaną z ciągiem . Może to być problem, jeśli format ciągu nie odpowiada przekazywanemu wartości LCID. Rozwiązania programu Excel utworzone przy użyciu narzędzi deweloperskie pakietu Office Visual Studio używać lcid 1033 (en-US) podczas przekazywania wszystkich danych. Program Excel wyświetla dane zgodnie z ustawieniami regionalnymi i językiem interfejsu użytkownika programu Excel. Visual Basic for Applications (VBA) działa również w ten sposób; Ciągi są sformatowane jako en-US i VBA prawie zawsze przekazuje 0 (neutralna dla języka) jako LCID. Na przykład poniższy kod VBA wyświetla poprawnie sformatowaną wartość dla 12 maja 2004 r., zgodnie z bieżącym ustawieniem ustawień regionalnych użytkownika:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Ten sam kod, gdy jest używany w rozwiązaniu utworzonym przy użyciu narzędzi programistycznym pakietu Office w programie Visual Studio i przekazany do programu Excel za pośrednictwem międzyplatopcyjnie com, generuje te same wyniki, gdy data jest sformatowana w stylu en-US.

 Na przykład:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet6":::

 Zawsze, gdy jest to możliwe, należy pracować z silnie typimi danymi zamiast literałami ciągów. Na przykład zamiast przechowywać datę w literału ciągu, należy zapisać ją jako , a następnie przekonwertować na obiekt do <xref:System.Double> <xref:System.DateTime> manipulowania.

 Poniższy przykład kodu przyjmuje datę wejdową użytkownika do komórki A5, zapisuje ją jako , a następnie konwertuje na obiekt do wyświetlenia w <xref:System.Double> <xref:System.DateTime> komórce A7. Komórka A7 musi być sformatowana, aby wyświetlić datę.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet7":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet7":::

### <a name="excel-worksheet-functions"></a>Funkcje arkusza programu Excel
 Nazwy funkcji arkusza są tłumaczone wewnętrznie dla większości wersji językowych programu Excel. Jednak ze względu na potencjalne problemy z językiem i międzyplatkową com zaleca się używanie w kodzie tylko nazw funkcji w języku angielskim.

### <a name="applications-that-use-external-data"></a>Aplikacje, które korzystają z danych zewnętrznych
 Każdy kod, który otwiera lub w inny sposób używa danych zewnętrznych, takich jak pliki, które zawierają wartości rozdzielane przecinkami (pliki CSV) wyeksportowane ze starszego systemu, może również mieć wpływ, jeśli takie pliki są eksportowane przy użyciu dowolnego formatu oprócz en-US. Nie ma to wpływu na dostęp do bazy danych, ponieważ wszystkie wartości powinny być w formacie binarnym, chyba że baza danych przechowuje daty jako ciągi lub wykonuje operacje, które nie używają formatu binarnego. Ponadto w przypadku konstruowania zapytań SQL przy użyciu danych z programu Excel może być konieczne upewninie się, że są one w formacie en-US, w zależności od funkcji, z których korzystasz.

## <a name="see-also"></a>Zobacz też

- [How to: Target the Office multilingual user interface (Jak kierować do wielojęzycznego interfejsu użytkownika pakietu Office)](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)