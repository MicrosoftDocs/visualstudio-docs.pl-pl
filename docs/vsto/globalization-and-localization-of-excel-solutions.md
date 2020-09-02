---
title: Globalizacja i lokalizacja rozwiązań programu Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f37ddcbbd3145fc96cd8081d7a1df524ef7ea8ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986056"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalizacja i lokalizacja rozwiązań programu Excel
  Ta sekcja zawiera informacje dotyczące specjalnych zagadnień dotyczących Microsoft Office rozwiązań programu Excel, które będą uruchamiane na komputerach, które mają ustawienia inne niż angielskie dla systemu Windows. Większość aspektów globalizacji i lokalizowania rozwiązań Microsoft Office jest taka sama, jak podczas tworzenia innych rodzajów rozwiązań za pomocą programu Visual Studio. Aby uzyskać ogólne informacje, zobacz [globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md).

 Domyślnie formanty hosta w programie Microsoft Office Excel działają prawidłowo w dowolnych ustawieniach regionalnych systemu Windows, o ile wszystkie dane, które są przesyłane lub manipulowane przy użyciu kodu zarządzanego, są sformatowane przy użyciu formatowania w języku angielskim (Stany Zjednoczone). W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , takie zachowanie jest kontrolowane przez środowisko uruchomieniowe języka wspólnego (CLR).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Formatowanie danych w programie Excel przy użyciu różnych ustawień regionalnych
 Należy sformatować wszystkie dane, które mają formatowanie z uwzględnieniem ustawień regionalnych, takie jak daty i waluta, przy użyciu formatu danych w języku angielskim (Stany Zjednoczone) (identyfikator ustawień regionalnych 1033) przed przekazaniem go do programu Microsoft Office Excel lub odczytanie danych z kodu w projekcie pakietu Office.

 Domyślnie podczas tworzenia rozwiązania biurowego w programie Visual Studio model obiektów programu Excel oczekuje na identyfikator ustawień regionalnych 1033 formatowanie danych (jest to również nazywane blokowaniem modelu obiektów do ustawień regionalnych 1033). To zachowanie jest zgodne ze sposobem, w jaki Visual Basic for Applications działa. Można jednak zmienić to zachowanie w rozwiązaniach pakietu Office.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Informacje o tym, jak model obiektów programu Excel ma zawsze oczekiwać identyfikatora ustawień regionalnych 1033
 Domyślnie w przypadku rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio nie mają one wpływ na ustawienia regionalne użytkownika końcowego i zawsze zachowują się tak, jakby ustawienia regionalne są w języku angielskim (Stany Zjednoczone). Na przykład w przypadku pobrania lub ustawienia <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> właściwości w programie Excel, dane muszą być sformatowane w sposób, w jaki jest oczekiwany identyfikator ustawień regionalnych 1033. Jeśli używasz innego formatu danych, możesz uzyskać nieoczekiwane wyniki.

 Mimo że w przypadku danych przesyłanych lub manipulowanych przez kod zarządzany jest używany format angielski (Stany Zjednoczone), program Excel interpretuje i wyświetla dane prawidłowo zgodnie z ustawieniami regionalnymi użytkownika końcowego. Program Excel może prawidłowo sformatować dane, ponieważ kod zarządzany przekazuje ustawienia regionalne o IDENTYFIKATORze 1033 wraz z danymi, co oznacza, że dane są w formacie angielskim (Stany Zjednoczone) i dlatego należy je ponownie sformatować, aby odpowiadały ustawieniu ustawień regionalnych użytkownika.

 Jeśli na przykład użytkownicy końcowi mają ustawione ustawienia regionalne niemiecki (Niemcy), oczekują od 29 czerwca 2005 do sformatowania w następujący sposób: 29.06.2005. Jeśli jednak rozwiązanie przekaże datę do programu Excel jako ciąg, należy sformatować datę zgodnie z formatem angielskim (Stany Zjednoczone): 6/29/2005. Jeśli komórka jest sformatowana jako komórka daty, program Excel wyświetli datę w formacie niemiecki (Niemcy).

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Przekaż inne identyfikatory ustawień regionalnych do modelu obiektów programu Excel
 Środowisko uruchomieniowe języka wspólnego (CLR) automatycznie przekazuje identyfikator ustawień regionalnych 1033 do wszystkich metod i właściwości w modelu obiektów programu Excel, który akceptuje dane zależne od ustawień regionalnych. Nie ma możliwości automatycznego zmiany tego zachowania dla wszystkich wywołań do modelu obiektów. Można jednak przekazać inny identyfikator ustawień regionalnych do konkretnej metody przy użyciu polecenia, <xref:System.Type.InvokeMember%2A> Aby wywołać metodę i przez przekazanie identyfikatora ustawień regionalnych do parametru *Culture* metody.

## <a name="localize-document-text"></a>Lokalizowanie tekstu dokumentu
 Dokument, szablon lub skoroszyt w projekcie prawdopodobnie zawiera tekst statyczny, który musi być zlokalizowany niezależnie od zestawu i innych zarządzanych zasobów. Prostym sposobem wykonania tej czynności jest wykonanie kopii dokumentu i przetłumaczenie tekstu przy użyciu programu Microsoft Office Word lub Microsoft Office Excel. Ten proces działa nawet wtedy, gdy nie wprowadzisz żadnych zmian w kodzie, ponieważ dowolna liczba dokumentów może być połączona z tym samym zestawem.

 Nadal musisz upewnić się, że jakakolwiek część kodu, która współdziała z tekstem dokumentu, nadal pasuje do języka tekstu, a zakładki, nazwane zakresy i inne pola wyświetlane uwzględniają wszelkie zmiany formatowania dokumentu pakietu Office, które były niezbędne do dostosowania do różnych gramatyki i długości tekstu. W przypadku szablonów dokumentów, które zawierają stosunkowo mały tekst, warto rozważyć przechowywanie tekstu w plikach zasobów, a następnie załadowanie tekstu w czasie wykonywania.

### <a name="text-direction"></a>Kierunek tekstu
 W programie Excel można ustawić właściwość arkusza do renderowania tekstu od prawej do lewej. Formanty hosta lub każda kontrolka, która ma `RightToLeft` Właściwość, która jest umieszczana w projektancie, automatycznie dopasowuje te ustawienia w czasie wykonywania. Program Word nie ma ustawienia dokumentu dla tekstu dwukierunkowego (po prostu zmieniasz wyrównanie tekstu), dlatego nie można mapować formantów do tego ustawienia. Zamiast tego należy ustawić wyrównanie tekstu dla każdej kontrolki. Można napisać kod w celu przechodzenia przez wszystkie kontrolki i wymusić renderowanie tekstu od prawej do lewej.

### <a name="change-culture"></a>Zmień kulturę
 Kod dostosowania na poziomie dokumentu zwykle udostępnia główny wątek interfejsu użytkownika programu Excel, dlatego wszelkie zmiany wprowadzone w kulturze wątku mają wpływ na wszystkie inne elementy działające w tym wątku. zmiana nie jest ograniczona do dostosowania.

 Formanty Windows Forms są inicjowane przed uruchomieniem dodatków VSTO na poziomie aplikacji przez aplikację hosta. W takich sytuacjach kulturę należy zmienić przed ustawieniem formantów interfejsu użytkownika.

## <a name="install-the-language-packs"></a>Zainstaluj pakiety językowe
 Jeśli masz ustawienia inne niż angielskie dla systemu Windows, możesz zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pakiety językowe, aby wyświetlić [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] komunikaty w tym samym języku co system Windows. Jeśli wszyscy użytkownicy końcowi korzystają z rozwiązań z ustawieniami innymi niż angielski dla systemu Windows, muszą mieć poprawny pakiet językowy, aby zobaczyć komunikaty środowiska uruchomieniowego w tym samym języku co system Windows. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Pakiety językowe są dostępne w [Centrum pobierania Microsoft](https://www.microsoft.com/download).

 Ponadto pakiety językowe .NET Framework redystrybucyjnej są niezbędne w przypadku komunikatów ClickOnce. Pakiety językowe .NET Framework są dostępne w [Centrum pobierania Microsoft](https://www.microsoft.com/download).

## <a name="regional-settings-and-excel-com-calls"></a>Ustawienia regionalne i wywołania COM programu Excel
 Za każdym razem, gdy zarządzany klient wywołuje metodę obiektu COM i musi przekazać informacje specyficzne dla kultury, robi to przy użyciu <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (ustawień regionalnych), które są zgodne z bieżącymi ustawieniami regionalnymi wątku. Bieżące ustawienia regionalne wątku są domyślnie dziedziczone z ustawień regionalnych użytkownika. Jednak w przypadku wywołania do modelu obiektów programu Excel z rozwiązania programu Excel utworzonego przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio format danych w języku angielskim (Stany Zjednoczone) (identyfikator ustawień regionalnych 1033) jest automatycznie przesyłany do modelu obiektów programu Excel. Przed przekazaniem Microsoft Office do programu Excel lub odczytaniem danych z kodu projektu należy sformatować wszystkie dane, które mają formatowanie z uwzględnieniem ustawień regionalnych, takie jak daty i waluta, przy użyciu formatu danych w języku angielskim (Stany Zjednoczone).

## <a name="considerations-for-storing-data"></a>Zagadnienia dotyczące przechowywania danych
 Aby upewnić się, że dane są poprawnie interpretowane i wyświetlane, należy również wziąć pod uwagę, że mogą wystąpić problemy, gdy aplikacja zapisuje dane, takie jak formuły arkusza programu Excel, w literałach ciągów (kodowane nieprawidłowo), a nie w obiektach o jednoznacznie określonym typie. Należy używać danych sformatowanych przy założeniu, że kultura niezmienna lub angielski (Stany Zjednoczone) (wartość LCID 1033).

### <a name="applications-that-use-string-literals"></a>Aplikacje korzystające z literałów ciągu
 Możliwe wartości, które mogą być zakodowane, obejmują literały dat, które są zapisywane w formacie angielskim (Stany Zjednoczone) i formuły arkusza programu Excel zawierające zlokalizowane nazwy funkcji. Inną możliwością może być zakodowany ciąg, który zawiera liczbę taką jak "1 000"; w niektórych kulturach jest interpretowane jako 1000, ale w innych kulturach reprezentuje jeden punkt zero. Obliczenia i porównania wykonane w nieprawidłowym formacie mogą spowodować nieprawidłowe dane.

 Program Excel interpretuje wszystkie ciągi zgodnie z identyfikatorem LCID, który jest przesyłany z ciągiem. Może to być problem, jeśli format ciągu nie odpowiada identyfikatorowi LCID, który został przesłany. Rozwiązania programu Excel utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio używają identyfikatora LCID 1033 (EN-US) podczas przekazywania wszystkich danych. Program Excel wyświetla dane zgodnie z ustawieniami regionalnymi i językiem interfejsu użytkownika programu Excel. Visual Basic for Applications (VBA) działa również w ten sposób; ciągi są sformatowane jako en-US, a język VBA prawie zawsze przekazuje 0 (neutralnie od języka) jako identyfikator LCID. Na przykład poniższy kod VBA wyświetla prawidłowo sformatowaną wartość dla 12 maja 2004, zgodnie z bieżącym ustawieniem regionalnym użytkownika:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Ten sam kod, gdy jest używany w rozwiązaniu utworzonym przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio i przeszedł do programu Excel za pomocą międzyoperacyjności modelu COM, tworzy te same wyniki, gdy data jest formatowana w stylu en-US.

 Na przykład:

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 Jeśli to możliwe, należy korzystać z danych o jednoznacznie określonym typie zamiast literałów ciągów. Na przykład zamiast przechowywania daty w literale ciągu, należy zapisać ją jako <xref:System.Double> , a następnie przekonwertować na <xref:System.DateTime> obiekt na potrzeby manipulowania.

 Poniższy przykład kodu pobiera datę, którą użytkownik wprowadza w komórce A5, zapisuje ją jako <xref:System.Double> , a następnie konwertuje ją na <xref:System.DateTime> obiekt do wyświetlenia w komórce Odp. Aby można było wyświetlić datę, należy sformatować komórkę "ODP".

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Funkcje arkusza programu Excel
 Nazwy funkcji arkusza są tłumaczone wewnętrznie w przypadku większości wersji językowych programu Excel. Jednak ze względu na potencjalne problemy związane z językiem i modelem COM zaleca się używanie tylko nazw funkcji w języku angielskim w kodzie.

### <a name="applications-that-use-external-data"></a>Aplikacje korzystające z danych zewnętrznych
 Każdy kod, który otwiera lub w inny sposób wykorzystuje dane zewnętrzne, takie jak pliki, które zawierają wartości rozdzielane przecinkami (pliki CSV) wyeksportowane z starszego systemu, może być również narażony, jeśli te pliki są eksportowane przy użyciu dowolnego formatu niż en-US. Nie ma to oddziaływać na dostęp do bazy danych, ponieważ wszystkie wartości powinny być w formacie binarnym, chyba że baza danych przechowuje daty jako ciągi lub wykonuje operacje, które nie używają formatu binarnego. Ponadto, jeśli tworzysz zapytania SQL przy użyciu danych z programu Excel, może być konieczne upewnienie się, że są one w formacie EN-US, w zależności od używanej funkcji.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: kierowanie wielojęzycznego interfejsu użytkownika pakietu Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)