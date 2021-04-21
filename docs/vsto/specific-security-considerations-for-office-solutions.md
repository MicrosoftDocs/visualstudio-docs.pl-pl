---
title: Specyficzne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office
description: Dowiedz się, w jaki sposób funkcje zabezpieczeń udostępniane przez platformę Microsoft .NET Framework i usługę Microsoft Office mogą pomóc w ochronie rozwiązań pakietu Office przed zagrożeniami bezpieczeństwa.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 58cd5f7a26be57ce0cb742e153d88ee455b2f85b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826112"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Specyficzne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office
  Funkcje zabezpieczeń udostępniane przez platformę Microsoft .NET Framework i usługę Microsoft Office mogą pomóc w ochronie rozwiązań pakietu Office przed możliwymi zagrożeniami bezpieczeństwa. W tym temacie wyjaśniono niektóre z tych zagrożeń i przedstawiono zalecenia, które ułatwiają ochronę przed nimi. Zawiera również informacje o tym, jak Microsoft Office zabezpieczeń wpływają na rozwiązania pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Zaufany kod jest ponownie kierunkowy w nowym, złośliwym dokumencie
 Osoba atakująca może pobrać zaufany kod przeznaczony do określonego celu, na przykład pobrać dane osobowe dla aplikacji do zatrudnienia i ponownie użyć go w innym dokumencie, takim jak arkusz. Kod nie wie, że oryginalny dokument nie jest uruchomiony i może otworzyć inne zagrożenia, takie jak ujawnienie danych osobowych lub wykonywanie kodu ze zwiększonymi uprawnieniami po otwarciu przez innego użytkownika. Alternatywnie osoba atakująca może zmodyfikować dane w arkuszu tak, aby podczas wysłania do ofiary zachowywała się ona nieoczekiwanie. Zmieniając wartości, formuły lub charakterystyki prezentacji arkusza połączonego z kodem, złośliwy użytkownik może zaatakować innego użytkownika, wysyłając zmodyfikowany plik. Użytkownicy mogą również uzyskać dostęp do informacji, których nie powinni zobaczyć, modyfikując wartości w arkuszu.

 Ponieważ zarówno lokalizacja zestawu, jak i lokalizacja dokumentu muszą mieć wystarczającą ilość dowodów do wykonania, ten atak nie jest łatwy do instalacji. Na przykład dokumenty w załącznikach wiadomości e-mail lub na niezaufanych serwerach intranetowych nie mają wystarczających uprawnień do uruchomienia.

 Aby ten atak był możliwy, sam kod musi być napisany w taki sposób, aby podejmować decyzje na podstawie potencjalnie niezaufanych danych. Przykładem jest utworzenie arkusza zawierającego ukrytą komórkę zawierającą nazwę serwera bazy danych. Użytkownik przesyła arkusz do strony ASPX, która próbuje nawiązać połączenie z tym serwerem przy użyciu uwierzytelniania SQL i zakodowanych haseł administratora. Osoba atakująca może zastąpić zawartość ukrytej komórki inną nazwą komputera i uzyskać hasło administratora systemu. Aby uniknąć tego problemu, nigdy nie należy kodować haseł i zawsze sprawdzać identyfikatory serwerów na wewnętrznej liście serwerów, które są znane jako dobre przed uzyskaniem dostępu do serwera.

### <a name="recommendations"></a>Zalecenia

- Zawsze sprawdzaj poprawność danych wejściowych i danych, niezależnie od tego, czy pochodzą od użytkownika, dokumentu, bazy danych, usługi internetowej czy dowolnego innego źródła.

- Należy zachować ostrożność podczas ujawniania określonych typów funkcji, takich jak pobieranie danych uprzywilejowanych w imieniu użytkownika i umieszczanie ich w niechronionym arkuszu.

- W zależności od typu aplikacji warto sprawdzić, czy oryginalny dokument jest uruchomiony przed wykonaniem kodu. Na przykład sprawdź, czy jest on uruchomiony z dokumentu przechowywanego w znanej, bezpiecznej lokalizacji.

- Dobrym pomysłem może być wyświetlenie ostrzeżenia po otworżeniu dokumentu, jeśli aplikacja wykonuje jakiekolwiek akcje uprzywilejowane. Możesz na przykład utworzyć ekran powitalny lub okno dialogowe uruchamiania z informacją, że aplikacja będzie mieć dostęp do danych osobowych i że użytkownik będzie mógł kontynuować lub anulować. Jeśli użytkownik końcowy otrzyma takie ostrzeżenie z pozornie owego dokumentu, będzie mógł zamknąć aplikację, zanim cokolwiek zostanie naruszone.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod jest blokowany przez osłonę modelu obiektów programu Outlook
 Microsoft Office ograniczyć kodowi możliwość używania niektórych właściwości, metod i obiektów w modelu obiektów. Ograniczając dostęp do tych obiektów, program Outlook pomaga zapobiegać używaniu modelu obiektów do złośliwych celów przez wirusy i wirusy wiadomości e-mail. Ta funkcja zabezpieczeń jest znana jako ochrona modelu obiektów programu Outlook. Jeśli dodatek VSTO próbuje użyć ograniczonej właściwości lub metody, gdy funkcja Object Model Guard jest włączona, program Outlook wyświetla ostrzeżenie o zabezpieczeniach, które umożliwia użytkownikowi zatrzymanie operacji lub umożliwia użytkownikowi udzielenie dostępu do właściwości lub metody na ograniczony czas. Jeśli użytkownik zatrzyma operację, dodatki VSTO programu Outlook utworzone przy użyciu rozwiązań pakietu Office Visual Studio zrzucą wyjątek <xref:System.Runtime.InteropServices.COMException> .

 Ochrona modelu obiektów może wpływać na dodatki VSTO na różne sposoby, w zależności od tego, czy program Outlook jest używany z programem Microsoft Exchange Server:

- Jeśli program Outlook nie jest używany z programem Exchange, administrator może włączyć lub wyłączyć funkcję ochrony modelu obiektów dla wszystkich dodatków VSTO na komputerze.

- Jeśli program Outlook jest używany z programem Exchange, administrator może włączyć lub wyłączyć funkcję ochrony modelu obiektów dla wszystkich dodatków VSTO na komputerze lub administrator może określić, że niektóre dodatki VSTO mogą być uruchamiane bez napotykania funkcji ochrony modelu obiektów. Administratorzy mogą również modyfikować zachowanie ochrony modelu obiektów dla niektórych obszarów modelu obiektów. Na przykład administratorzy mogą automatycznie zezwalać dodatekom VSTO na programowe wysyłanie wiadomości e-mail, nawet jeśli włączono funkcję ochrony modelu obiektów.

  Począwszy od programu Outlook 2007, zachowanie ochrony modelu obiektów zostało zmienione, aby poprawić środowisko dewelopera i użytkownika przy jednoczesnym zachowaniu bezpieczeństwa programu Outlook. Aby uzyskać więcej informacji, zobacz Code security changes in Outlook 2007 (Zmiany zabezpieczeń kodu [w programie Outlook 2007).](/previous-versions/office/developer/office-2007/bb226709(v=office.12))

### <a name="minimize-object-model-guard-warnings"></a>Minimalizowanie ostrzeżeń ochrony modelu obiektu
 Aby uniknąć ostrzeżeń o zabezpieczeniach podczas używania ograniczonych właściwości i metod, upewnij się, że dodatek VSTO uzyskuje obiekty programu Outlook z pola klasy `Application` `ThisAddIn` w projekcie. Aby uzyskać więcej informacji na temat tego pola, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md)

 Tylko obiekty programu Outlook uzyskane z tego obiektu mogą być zaufane przez strażnika modelu obiektów. Z kolei obiekty, które są uzyskiwane z nowego obiektu, nie są zaufane, a ograniczone właściwości i metody będą zgłaszać ostrzeżenia o zabezpieczeniach, jeśli ochrona `Microsoft.Office.Interop.Outlook.Application` modelu obiektów jest włączona.

 Poniższy przykład kodu wyświetla ostrzeżenie o zabezpieczeniach, jeśli włączono ochronę modelu obiektu. Właściwość `To` klasy jest `Microsoft.Office.Interop.Outlook.MailItem` ograniczona przez osłonę modelu obiektów. Obiekt jest niezaufany, ponieważ kod pobiera go z obiektu utworzonego przy użyciu nowego operatora, zamiast `Microsoft.Office.Interop.Outlook.MailItem` `Microsoft.Office.Interop.Outlook.Application` pobierać go z pola  `Application` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet1":::

 W poniższym przykładzie kodu pokazano, jak używać właściwości z ograniczeniami do obiektu, który jest zaufany `Microsoft.Office.Interop.Outlook.MailItem` przez strażnik modelu obiektów. Kod używa pola `Application` zaufanego w celu uzyskania wartości `Microsoft.Office.Interop.Outlook.MailItem` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet2":::

> [!NOTE]
> Jeśli program Outlook jest używany z programem Exchange, uzyskanie wszystkich obiektów programu Outlook z programu nie gwarantuje, że dodatek VSTO będzie mógł uzyskać dostęp do całego modelu obiektów `ThisAddIn.Application` programu Outlook. Jeśli na przykład administrator programu Exchange ustawia program Outlook tak, aby automatycznie odrzucał wszystkie próby uzyskania dostępu do informacji o adresach przy użyciu modelu obiektów programu Outlook, program Outlook nie zezwoli poprzedniemu przykładowi kodu na dostęp do właściwości Do, mimo że przykładowy kod używa zaufanego `ThisAddIn.Application` pola.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Określanie, które dodatki mają być zaufane podczas korzystania z programu Exchange
 Gdy program Outlook jest używany z programem Exchange, administratorzy mogą określić, że niektóre dodatki VSTO mogą być uruchamiane bez napotkania ochrony modelu obiektu. Dodatki VSTO programu Outlook utworzone przy użyciu rozwiązań pakietu Office Visual Studio nie mogą być zaufane indywidualnie; Mogą być one zaufane tylko jako grupa.

 Program Outlook ufa dodatku VSTO na podstawie kodu skrótu biblioteki DLL punktu wejścia dodatku VSTO. Wszystkie dodatki VSTO programu Outlook, które są docelowe dla obiektu , używają tej [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] samej biblioteki DLL punktu wejścia *(VSTOLoader.dll*). Oznacza to, że jeśli administrator ufa dowolnemu dodatku VSTO, który jest przeznaczony do uruchomienia bez napotkania ochrony modelu obiektu, wszystkie inne dodatki VSTO, które są również [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zaufane. Aby uzyskać więcej informacji na temat zaufania do określonych dodatków VSTO do uruchomienia bez napotkania funkcji ochrony modelu obiektów, zobacz Określanie metody używanej przez program Outlook do zarządzania funkcjami [zapobiegania wirusom.](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12))

## <a name="permission-changes-do-not-take-effect-immediately"></a>Zmiany uprawnień nie są natychmiast obowiązywać
 Jeśli administrator dostosuje uprawnienia do dokumentu lub zestawu, użytkownicy muszą zamknąć, a następnie ponownie uruchomić wszystkie aplikacje pakietu Office, aby te zmiany zostały wymuszone.

 Inne aplikacje, które Microsoft Office aplikacji, mogą również uniemożliwić wymuszanie nowych uprawnień. Po zmianie zasad zabezpieczeń użytkownicy powinni zamknąć wszystkie aplikacje korzystające z pakietu Office, hostowane lub autonomiczne.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Ustawienia Centrum zaufania w Microsoft Office nie mają wpływu na dodatki ani dostosowania na poziomie dokumentu
 Użytkownicy mogą uniemożliwić ładowanie dodatków VSTO, ustawiając opcję w **Centrum zaufania.** Te ustawienia zaufania nie mają jednak wpływu na dodatki VSTO i dostosowania na poziomie dokumentu utworzone przy użyciu rozwiązań pakietu Office w usłudze Visual Studio.

 Jeśli użytkownik uniemożliwia ładowanie dodatków VSTO przy użyciu Centrum **zaufania,** następujące typy dodatków VSTO nie zostaną załadowane:

- Zarządzane i niezaładowane dodatki COM VSTO.

- Zarządzane i nieza zarządzanie dokumenty inteligentne.

- Zarządzane i niezaładowane dodatki VSTO automatyzacji.

- Zarządzane i nieza zarządzanych składników danych w czasie rzeczywistym.

  Poniższe procedury opisują sposób,  w jaki użytkownicy mogą używać Centrum zaufania do ograniczania ładowania dodatków VSTO w firmach Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i Microsoft Office 2010. Te procedury nie mają wpływu na dodatki VSTO ani dostosowania utworzone przy użyciu narzędzi programistycznych pakietu Office w Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>Aby wyłączyć dodatki VSTO w programach Microsoft Office 2010 i [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Microsoft

1. Wybierz **kartę** Plik.

2. Wybierz przycisk *ApplicationName* **Options (Opcje nazwy aplikacji).**

3. W okienku kategorii wybierz pozycję **Centrum zaufania.**

4. W okienku szczegółów wybierz pozycję **Ustawienia Centrum zaufania.**

5. W okienku kategorii wybierz pozycję **Dodatki**.

6. W okienku szczegółów wybierz pozycję **Wymagaj,** aby dodatki aplikacji było podpisane przez zaufanego wydawcę, lub pozycję Wyłącz wszystkie **dodatki aplikacji.**

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
