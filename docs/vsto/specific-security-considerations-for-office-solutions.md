---
title: Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1a40fe9329061b457fb2038399324818ec69e43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629082"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office
  Funkcjach zabezpieczeń zapewnianych przez program Microsoft .NET Framework i Microsoft Office może pomóc chronić swoje rozwiązania pakietu Office na potencjalne zagrożenia. W tym temacie opisano niektóre z tych zagrożeń i zapewnia zalecenia, aby zapewnić ochronę przed nimi. Zawiera także informacje o wpływie ustawienia zabezpieczeń Microsoft Office na rozwiązań pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Zaufanego kodu jest przeznaczenie w nowych, złośliwych dokument
 Może zająć zaufany kod, który jest przeznaczona dla jednego określonego celu, na przykład pobranie informacji osobistych, aplikacji zatrudnienia, a użyć go ponownie w innym dokumencie, takie jak arkusz. Kod nie wiedzieć, że oryginalny dokument nie jest uruchomiony i może otworzyć innych zagrożeń, takich jak ujawniać dane osobowe lub wykonywania kodu za pomocą uprawnień zwiększone, gdy otwarty przez innego użytkownika. Alternatywnie osoba atakująca dane można modyfikować w arkuszu taki sposób, że gdy wysyłane do ofiary, działa nieoczekiwanie. Zmieniając wartości, formuły lub cechy prezentacji arkuszu połączone z kodu, jest to możliwe, złośliwy użytkownik na ataki innego użytkownika, wysyłając zmodyfikowanego pliku. Istnieje również możliwość użytkownikom uzyskiwanie dostępu do informacji, który nie powinien wyświetlić przez zmodyfikowanie wartości w tym skoroszycie.

 Ponieważ lokalizacja zestawu i lokalizacji dokumentu musi mieć wystarczające dowody do wykonania, ataku nie jest łatwe do zainstalowania. Na przykład dokumenty w załączniki wiadomości e-mail lub w niezaufanej intranetowych serwerów ma wystarczających uprawnień do uruchomienia.

 Aby umożliwić atak, sam kod musi być napisana w taki sposób, że to sprawia, że decyzje na podstawie danych potencjalnie niezaufana. Przykładem jest utworzenie arkusza zawierającej ukryte komórkę, która zawiera nazwę serwera bazy danych. Użytkownik przesyła arkusza do strony ASPX, który próbuje nawiązać połączenie z tym serwerem przy użyciu uwierzytelniania SQL i zakodowane hasło administratora systemu. Osoba atakująca może Zamień zawartość komórek ukryte inną nazwę komputera i Uzyskaj hasło administratora systemu. Aby uniknąć tego problemu, nigdy nie kodować sprzętowo hasła, Zawsze sprawdzaj identyfikatorów serwera względem wewnętrzną listę serwerów, które są znane jako dobre przed uzyskaniem dostępu do serwera.

### <a name="recommendations"></a>Zalecenia

-   Zawsze weryfikowały dane wejściowe i dane, czy jest określany na podstawie użytkownika, dokument, bazy danych, usługi sieci web lub dowolnego innego źródła.

-   Należy zachować ostrożność udostępnianie określone typy funkcji, takich jak pobieranie danych uprzywilejowanego w imieniu użytkownika i umieszczając go w niechronionego arkusza.

-   W zależności od typu aplikacji może mieć sens, aby sprawdzić, czy działa oryginalnego dokumentu, przed wykonaniem jakiegokolwiek kodu. Na przykład sprawdzić, czy działa on od dokumentu przechowywanego w lokalizacji znanych, bezpiecznych.

-   Może to być dobry pomysł, aby wyświetlić ostrzeżenie, jeśli dokument zostanie otwarty, jeśli aplikacja wykonuje żadnych uprzywilejowanych akcji. Na przykład utworzyć ekran powitalny lub okno dialogowe uruchamiania informujący o tym, że aplikacja będzie dostęp do informacji osobistych i użytkownik powinien wybrać kontynuować, lub przycisk Anuluj. Jeśli użytkownik końcowy pobiera takie ostrzeżenie z dokumentem pozornie nieszkodliwie, użytkownik będzie można zamknąć aplikację, zanim wszystko zostanie naruszony.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod jest zablokowany przez strażnik modelu obiektów programu Outlook
 Microsoft Office, można ograniczyć kodu korzystania z niektórych właściwości, metod i obiekty w modelu obiektów. Przez ograniczenie dostępu do tych obiektów, program Outlook pomaga zapobiec za pomocą modelu obiektów do złośliwych celów robaki poczty e-mail i wirusami. Ta funkcja zabezpieczeń jest określany jako strażnik modelu obiektów programu Outlook. Jeśli dodatku narzędzi VSTO próbuje użyć ograniczone właściwości lub metody, przy włączonym strażnik modelu obiektów, program Outlook wyświetli ostrzeżenie, który umożliwia użytkownikowi zatrzymać operację lub umożliwia użytkownikowi udzielać dostępu do właściwości lub metody przez ograniczony okres t edytora IME. Jeśli użytkownik zatrzymuje operację, dodatków narzędzi VSTO dla programu Outlook utworzone za pomocą rozwiązań pakietu Office w programie Visual Studio będzie zgłaszać <xref:System.Runtime.InteropServices.COMException>.

 Strażnik modelu obiektów może mieć wpływ na dodatków narzędzi VSTO na różne sposoby, w zależności od tego, czy program Outlook jest używany z programem Microsoft Exchange Server:

- Jeśli program Outlook nie jest używany z programem Exchange, administratora można włączyć lub wyłączyć strażnik modelu obiektów dla wszystkich dodatków narzędzi VSTO na komputerze.

- Jeśli program Outlook jest używany z programem Exchange, administrator może włączyć lub wyłączyć strażnik modelu obiektów dla wszystkich dodatków narzędzi VSTO na komputerze, lub administrator może określić, że niektóre dodatków narzędzi VSTO dla programów może działać bez napotkania strażnik modelu obiektów. Administratorzy mogą również modyfikować zachowanie strażnik modelu obiektów dla niektórych obszarów modelu obiektów. Na przykład Administratorzy automatycznie umożliwia dodatków narzędzi VSTO dla programów do wysyłania wiadomości e-mail programowo, nawet jeśli jest włączona strażnik modelu obiektów.

  Począwszy od programu Outlook 2007, zachowanie strażnik modelu obiektów został zmieniony na ulepszaniu środowiska programistów i użytkowników, jednocześnie zachowując bezpieczeństwo programu Outlook. Aby uzyskać więcej informacji, zobacz [kodu zmiany zabezpieczeń w programie Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).

### <a name="minimize-object-model-guard-warnings"></a>Minimalizuj ostrzeżenia guard modelu obiektu
 Aby uniknąć wyświetlania ostrzeżenia o zabezpieczeniach podczas korzystania z ograniczeniami właściwości i metod, upewnij się, dodatku narzędzi VSTO dla programów uzyskuje obiektów programu Outlook z `Application` pole `ThisAddIn` klasy w projekcie. Aby uzyskać więcej informacji na temat tego pola, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

 Strażnik modelu obiektów mogą ufać tylko obiekty programu Outlook uzyskany z tego obiektu. Z kolei obiekty, które są uzyskiwane z nową `Microsoft.Office.Interop.Outlook.Application` obiektu nie są zaufane, a ograniczone właściwości i metody zgłosi ostrzeżenia o zabezpieczeniach po włączeniu strażnik modelu obiektów.

 Poniższy kod wyświetla ostrzeżenie o zabezpieczeniach, jeśli włączono strażnik modelu obiektów. `To` Właściwość `Microsoft.Office.Interop.Outlook.MailItem` klasy jest ograniczony przez strażnik modelu obiektów. `Microsoft.Office.Interop.Outlook.MailItem` Obiektu nie jest zaufany, ponieważ kod pobiera z `Microsoft.Office.Interop.Outlook.Application` utworzonego za pomocą **nowe** operatora, zamiast go z uzyskiwania `Application` pola.

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Poniższy przykład kodu pokazuje, jak za pomocą zastrzeżonego właściwość `Microsoft.Office.Interop.Outlook.MailItem` obiektu, który jest zaufany przez strażnik modelu obiektów. Kod używa zaufanej `Application` pola, aby uzyskać `Microsoft.Office.Interop.Outlook.MailItem`.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
>  Jeśli program Outlook jest używany z programem Exchange, uzyskiwanie wszystkich obiektów programu Outlook z `ThisAddIn.Application` nie gwarantuje, że dodatku narzędzi VSTO dla programów będzie mogli korzystać z całej modelu obiektów programu Outlook. Na przykład jeśli administrator programu Exchange Outlook automatycznie ustawia Odmów wszystkie próby uzyskania dostępu do informacji dotyczących adresów za pomocą modelu obiektów programu Outlook, a następnie program Outlook nie pozwoli na poprzednim przykładzie kodu w celu dostępu do właściwości na, mimo że w przykładzie kodu użyto zaufanej `ThisAddIn.Application` pola.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Określ, które dodatków do sytuacji, gdy program Exchange jest używany
 Gdy program Outlook jest używany z programem Exchange, Administratorzy mogą określić, że niektóre dodatków narzędzi VSTO dla programów może działać bez napotkania strażnik modelu obiektów. Program Outlook dodatków narzędzi VSTO utworzone za pomocą rozwiązań pakietu Office w programie Visual Studio nie jest zaufany. może być tylko zaufane jako grupa.

 Program Outlook ufa dodatku narzędzi VSTO na podstawie kodu wyznaczania wartości skrótu, biblioteki DLL punktu wejścia dodatku narzędzi VSTO dla programu. Wszystkie Outlook dodatków narzędzi VSTO przeznaczonych dla [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używać tej samej bibliotece DLL punktu wejścia (*VSTOLoader.dll*). Oznacza to, że jeśli administrator ufa wszelkie dodatku narzędzi VSTO przeznaczonego dla [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do uruchomienia nie powodując strażnik modelu obiektów, a następnie wszystkich innych dodatków narzędzi VSTO dla programów, których platformą docelową [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] są także zaufane. Aby uzyskać więcej informacji na temat ufające określonych dodatków narzędzi VSTO do uruchomienia nie powodując strażnik modelu obiektów, zobacz [Określ metodę Outlook używa do zarządzania funkcji ochrony przed wirusami](http://go.microsoft.com/fwlink/?LinkId=128773).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Zmiany uprawnień nie obowiązywać natychmiast
 Jeśli administrator dostosowuje uprawnienia do dokumentu lub zestawu, użytkowników, należy zamknąć i uruchom ponownie wszystkie aplikacje pakietu Office dla tych zmian, które zostaną wymuszone.

 Inne aplikacje, które hostują aplikacje Microsoft Office, mogą również uniemożliwić nowe uprawnienia, jakie są wymuszane. Użytkownikom należy zamknąć wszystkich aplikacji korzystających z pakietu Office, hostowanych lub autonomicznych, po zmianie zasad zabezpieczeń.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Ustawienia Centrum zaufania systemu Microsoft Office nie wpływają na dodatków lub dostosowań na poziomie dokumentu
 Użytkownicy mogą uniemożliwić dodatków narzędzi VSTO ładowania, ustawiając opcję w **Centrum zaufania**. Jednak dodatków narzędzi VSTO dla programów i dostosowań poziomu dokumentu utworzone za pomocą rozwiązań pakietu Office w programie Visual Studio nie dotyczy tych ustawień zaufania.

 Jeśli użytkownik uniemożliwia dodatków narzędzi VSTO ładowania przy użyciu **Centrum zaufania**, nie załaduje dodatków narzędzi VSTO dla następujących typów:

- Zarządzane i niezarządzane COM dodatków narzędzi VSTO.

- Dokumenty inteligentne zarządzanych i niezarządzanych.

- Zarządzane i niezarządzane automatyzacji dodatków narzędzi VSTO.

- Składniki zarządzane i niezarządzane danych w czasie rzeczywistym.

  W poniższych procedurach opisano sposób używania przez użytkowników **Centrum zaufania** ograniczyć dodatków narzędzi VSTO ładowania w usłudze Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i Microsoft Office 2010. Procedury te nie wpływają na dodatków narzędzi VSTO dla programów lub dostosowania utworzone za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Aby wyłączyć dodatków narzędzi VSTO dla programów w pakiecie Microsoft Office 2010 i Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikacji

1.  Wybierz **pliku** kartę.

2.  Wybierz *ApplicationName* **opcje** przycisku.

3.  W okienku kategorii wybierz **Centrum zaufania**.

4.  W okienku szczegółów wybierz **ustawienia Centrum zaufania**.

5.  W okienku kategorii wybierz **Add-ins**.

6.  W okienku szczegółów wybierz **dodatki wymagają aplikacji były podpisane przez zaufanego wydawcę** lub **Wyłącz wszystkie dodatki aplikacji**.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
