---
title: Szczególne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office
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
ms.openlocfilehash: 571b604b87fb7fac4e78c83a791c265d910fae94
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985583"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Szczególne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office
  Funkcje zabezpieczeń zapewniane przez Microsoft .NET Framework i Microsoft Office mogą pomóc w ochronie rozwiązań pakietu Office przed potencjalnymi zagrożeniami bezpieczeństwa. W tym temacie objaśniono niektóre z tych zagrożeń i udostępniono zalecenia ułatwiające ochronę przed nimi. Zawiera również informacje dotyczące sposobu, w jaki Microsoft Office ustawienia zabezpieczeń mają wpływ na rozwiązania pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Kod zaufany jest przeznaczeniem w nowym, złośliwym dokumencie
 Osoba atakująca może przejąć zaufany kod, który jest przeznaczony do jednego określonego celu, na przykład pobierając informacje osobiste dla aplikacji zatrudniania, a następnie użyć go ponownie w innym dokumencie, takim jak arkusz. Kod nie wie, że oryginalny dokument nie jest uruchomiony i może otworzyć inne zagrożenia, takie jak ujawnienie informacji osobistych lub wykonywanie kodu z zwiększonymi uprawnieniami, w przypadku otwarcia przez innego użytkownika. Alternatywnie, osoba atakująca może modyfikować dane w arkuszu, tak jak w przypadku wysłania do ofiary, działa nieoczekiwanie. Zmieniając wartości, formuły lub właściwości prezentacji arkusza połączonego z kodem, istnieje możliwość, że złośliwy użytkownik może zaatakować innego użytkownika, wysyłając zmodyfikowany plik. Może być również możliwe, aby użytkownicy mieli dostęp do informacji, których nie widzisz, modyfikując wartości w arkuszu.

 Ponieważ zarówno lokalizacja zestawu, jak i lokalizacja dokumentu muszą mieć wystarczające dowody do wykonania, atak nie jest łatwy do zainstalowania. Na przykład dokumenty w załącznikach wiadomości e-mail lub na niezaufanych serwerach intranetowych nie mają wystarczających uprawnień do uruchomienia.

 Aby umożliwić atak, sam kod musi być zapisany w taki sposób, że podejmuje decyzje na podstawie potencjalnie niezaufanych danych. Przykładem jest Tworzenie arkusza z ukrytą komórką zawierającą nazwę serwera bazy danych. Użytkownik przesyła arkusz do strony ASPX, która próbuje nawiązać połączenie z tym serwerem przy użyciu uwierzytelniania SQL i zakodowanego hasła administratora systemu. Osoba atakująca może zastąpić zawartość ukrytej komórki inną nazwą komputera i uzyskać hasło administratora systemu. Aby uniknąć tego problemu, nigdy nie obciążaj hasła i zawsze sprawdzaj identyfikatory serwera względem wewnętrznej listy serwerów, które są znane jako dobre przed uzyskaniem dostępu do serwera.

### <a name="recommendations"></a>Mając

- Zawsze sprawdzaj dane wejściowe i dane, niezależnie od tego, czy pochodzą one od użytkownika, dokumentu, bazy danych, usługi sieci Web, czy też innego źródła.

- Należy zachować ostrożność podczas ujawniania określonych typów funkcji, takich jak uzyskiwanie uprzywilejowanych danych w imieniu użytkownika i umieszczanie go w niechronionym arkuszu.

- W zależności od typu aplikacji warto upewnić się, że oryginalny dokument jest uruchomiony przed wykonaniem dowolnego kodu. Na przykład sprawdź, czy jest on uruchomiony z dokumentu przechowywanego w znanej, bezpiecznej lokalizacji.

- Dobrym pomysłem jest wyświetlenie ostrzeżenia w przypadku otwarcia dokumentu, jeśli aplikacja wykonuje jakiekolwiek uprzywilejowane akcje. Na przykład możesz utworzyć ekran powitalny lub okno dialogowe uruchamiania informujące, że aplikacja będzie uzyskiwać dostęp do informacji osobistych i czy użytkownik zdecyduje się na kontynuowanie lub anulowanie. Jeśli użytkownik końcowy otrzyma takie ostrzeżenie z pozornie nieszkodliweego dokumentu, może zakończyć działanie aplikacji przed naruszeniem jakichkolwiek zmian.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod jest blokowany przez funkcję ochrony modelu obiektów programu Outlook
 Microsoft Office może ograniczyć kod z używania określonych właściwości, metod i obiektów w modelu obiektów. Ograniczając dostęp do tych obiektów, program Outlook pomaga zapobiegać robakom i wirusom poczty e-mail za pomocą modelu obiektów do złośliwych celów. Ta funkcja zabezpieczeń jest znana jako ochrona modelu obiektów programu Outlook. Jeśli dodatek VSTO próbuje użyć właściwości lub metody z ograniczeniami, podczas gdy włączona jest funkcja ochrony modelu obiektów, w programie Outlook zostanie wyświetlone ostrzeżenie o zabezpieczeniach, które umożliwi użytkownikowi zatrzymanie operacji lub umożliwienie użytkownikowi udzielenia dostępu do właściwości lub metody przez ograniczony czas t Konwersje. Jeśli użytkownik zatrzyma operację, Dodatki programu Outlook VSTO utworzone przy użyciu rozwiązań pakietu Office w programie Visual Studio wygenerują <xref:System.Runtime.InteropServices.COMException>.

 Funkcja model obiektów może mieć wpływ na dodatki VSTO na różne sposoby, w zależności od tego, czy program Outlook jest używany z programem Microsoft Exchange Server:

- Jeśli program Outlook nie jest używany z programem Exchange, administrator może włączyć lub wyłączyć ochronę modelu obiektów dla wszystkich dodatków narzędzi VSTO na komputerze.

- Jeśli program Outlook jest używany z programem Exchange, administrator może włączyć lub wyłączyć ochronę modelu obiektów dla wszystkich dodatków VSTO na komputerze lub administrator może określić, że niektóre dodatki narzędzi VSTO mogą być uruchamiane bez napotkania funkcji ochrony modelu obiektów. Administratorzy mogą również modyfikować zachowanie funkcji ochrony modelu obiektów dla niektórych obszarów modelu obiektów. Na przykład Administratorzy mogą automatycznie zezwalać dodatkom VSTO na programowe wysyłanie poczty e-mail, nawet jeśli włączono ochronę modelu obiektów.

  Począwszy od programu Outlook 2007, zachowanie funkcji ochrony modelu obiektów zostało zmienione w celu poprawy środowiska programistycznego i użytkownika w celu zapewnienia bezpieczeństwa programu Outlook. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń kodu w programie Outlook 2007](/previous-versions/office/developer/office-2007/bb226709(v=office.12)).

### <a name="minimize-object-model-guard-warnings"></a>Minimalizuj ostrzeżenia ochrony modelu obiektów
 Aby uniknąć ostrzeżeń dotyczących zabezpieczeń w przypadku używania właściwości i metod z ograniczeniami, upewnij się, że dodatek VSTO Pobiera obiekty programu Outlook z pola `Application` klasy `ThisAddIn` w projekcie. Aby uzyskać więcej informacji na temat tego pola, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 Funkcja ochrony modelu obiektów może ufać tylko obiektom programu Outlook uzyskanym z tego obiektu. W przeciwieństwie do obiektów, które są uzyskiwane z nowego obiektu `Microsoft.Office.Interop.Outlook.Application` nie są zaufane, a właściwości i metody z ograniczeniami spowodują wygenerowanie ostrzeżeń zabezpieczeń, jeśli włączono ochronę modelu obiektów.

 Poniższy przykład kodu wyświetla ostrzeżenie o zabezpieczeniach, jeśli włączona jest funkcja Guard modelu obiektów. Właściwość `To` klasy `Microsoft.Office.Interop.Outlook.MailItem` jest ograniczona przez ochronę modelu obiektów. Obiekt `Microsoft.Office.Interop.Outlook.MailItem` jest niezaufany, ponieważ kod pobiera go z `Microsoft.Office.Interop.Outlook.Application`, który jest tworzony przy użyciu operatora **New** , zamiast uzyskać go z pola `Application`.

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Poniższy przykład kodu demonstruje, jak użyć właściwości ograniczone do obiektu `Microsoft.Office.Interop.Outlook.MailItem`, który jest zaufany przez ochronę modelu obiektów. Kod używa pola zaufane `Application`, aby uzyskać `Microsoft.Office.Interop.Outlook.MailItem`.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Jeśli program Outlook jest używany z programem Exchange, uzyskanie wszystkich obiektów programu Outlook z `ThisAddIn.Application` nie gwarantuje, że dodatek VSTO będzie w stanie uzyskać dostęp do całego modelu obiektów programu Outlook. Na przykład, jeśli administrator programu Exchange ustawi program Outlook, aby automatycznie odmówił wszystkich prób dostępu do informacji o adresie przy użyciu modelu obiektów programu Outlook, program Outlook nie zezwoli na poprzedni przykład kodu, aby uzyskać dostęp do właściwości do, nawet jeśli przykład kodu używa pole zaufane `ThisAddIn.Application`.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Określ, które dodatki mają być zaufane w przypadku korzystania z programu Exchange
 Gdy program Outlook jest używany z programem Exchange, Administratorzy mogą określić, że niektóre dodatki narzędzi VSTO mogą być uruchamiane bez napotkania funkcji ochrony modelu obiektów. Dodatki narzędzi VSTO programu Outlook utworzone przy użyciu rozwiązań pakietu Office w programie Visual Studio nie mogą być zaufane indywidualnie; mogą być zaufane tylko jako Grupa.

 Program Outlook ufa Dodatekowi VSTO na podstawie kodu skrótu biblioteki DLL punktu wejścia dodatku VSTO. Wszystkie dodatki programu Outlook VSTO przeznaczone dla [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używają tej samej biblioteki DLL punktu wejścia (*VSTOLoader. dll*). Oznacza to, że jeśli administrator ufa każdemu dodatkowi narzędziu VSTO, który jest przeznaczony dla [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do uruchomienia bez napotkania funkcji ochrony modelu obiektów, wszystkie dodatki narzędzi VSTO, które są przeznaczone dla [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], również są zaufane. Aby uzyskać więcej informacji na temat ufania konkretnym dodatkom narzędzia VSTO do uruchamiania bez napotkania funkcji ochrony modelu obiektów, zobacz [Określanie metody stosowanej przez program Outlook do zarządzania funkcjami ochrony przed wirusami](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12)).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Zmiany uprawnień nie zaczynają obowiązywać natychmiast
 Jeśli administrator dostosowuje uprawnienia do dokumentu lub zestawu, użytkownicy muszą zamknąć, a następnie ponownie uruchomić wszystkie aplikacje pakietu Office, aby wprowadzić te zmiany.

 Inne aplikacje, które obsługują aplikacje Microsoft Office, mogą również uniemożliwić wymuszanie nowych uprawnień. Użytkownicy powinni zamknąć wszystkie aplikacje korzystające z pakietu Office, hostowane lub autonomiczne, gdy zasady zabezpieczeń są zmieniane.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Ustawienia Centrum zaufania w systemie Microsoft Office nie mają wpływu na dodatki lub dostosowania na poziomie dokumentu
 Użytkownicy mogą zapobiegać załadowaniu dodatków VSTO przez ustawienie opcji w **Centrum zaufania**. Jednak te ustawienia zaufania nie wpływają na dodatki narzędzi VSTO i dostosowania na poziomie dokumentu utworzone przy użyciu rozwiązań pakietu Office w programie Visual Studio.

 Jeśli użytkownik nie zezwala na ładowanie dodatków VSTO przy użyciu **Centrum zaufania**, następujące typy dodatków narzędzi VSTO nie zostaną załadowane:

- Zarządzane i niezarządzane dodatki narzędzi VSTO dla modelu COM.

- Zarządzane i niezarządzane dokumenty inteligentne.

- Zarządzane i niezarządzane dodatki narzędzi VSTO dla automatyzacji.

- Zarządzane i niezarządzane składniki danych w czasie rzeczywistym.

  W poniższych procedurach opisano sposób, w jaki użytkownicy mogą korzystać z **Centrum zaufania** w celu ograniczenia ładowania dodatków VSTO w programie Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i Microsoft Office 2010. Te procedury nie wpływają na dodatki i dostosowania narzędzia VSTO utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice_15_shortvstoincludesoffice-15-short-mdmd-applications"></a>Aby wyłączyć dodatki narzędzi VSTO w Microsoft Office 2010 i aplikacji [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] firmy Microsoft

1. Wybierz kartę **plik** .

2. Wybierz przycisk **Opcje** ApplicationName.

3. W okienku Kategorie wybierz pozycję **Centrum zaufania**.

4. W okienku szczegółów wybierz pozycję **Ustawienia Centrum zaufania**.

5. W okienku Kategorie wybierz pozycję **Dodatki**.

6. W okienku szczegółów wybierz opcję **Wymagaj podpisania dodatków aplikacji przez zaufanego wydawcę** lub **Wyłącz wszystkie dodatki aplikacji**.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
