---
title: Tworzenie niestandardowego programu inicjującego wyświetlającego monit o zasadach ochrony prywatności
description: Dowiedz się, jak skonfigurować aplikacje ClickOnce do automatycznej aktualizacji, gdy zestawy z nowszymi wersjami plików i wersjami zestawu staną się dostępne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96cfbf8693ce23dbc0b0584c7742607224aeab4f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216946"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Przewodnik: Tworzenie niestandardowego programu inicjującego wyświetlającego monit o zasadach ochrony prywatności
Aplikacje ClickOnce można skonfigurować do automatycznego aktualizowania, gdy zestawy z nowszymi wersjami plików i wersjami zestawu staną się dostępne. Aby upewnić się, że klienci wyrażają zgodę na takie zachowanie, możesz wyświetlić do nich monit o prywatność. Następnie mogą zdecydować, czy udzielić uprawnienia aplikacji do automatycznej aktualizacji. Jeśli aplikacja nie jest dozwolona do automatycznej aktualizacji, nie zostanie zainstalowana.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Program Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Okno dialogowe Tworzenie zgody na aktualizację
 Aby wyświetlić monit o prywatność, należy utworzyć aplikację, która prosi czytelnika o zgodę na automatyczne aktualizacje aplikacji.

#### <a name="to-create-a-consent-dialog-box"></a>Aby utworzyć okno dialogowe zgody

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** kliknij pozycję **Windows**, a następnie kliknij pozycję **WindowsFormsApplication**.

3. W polu **Nazwa** wpisz **ConsentDialog**, a następnie kliknij przycisk **OK**.

4. W projektancie kliknij formularz.

5. W oknie **Właściwości** Zmień właściwość **Text** na **okno dialogowe Aktualizowanie zgody**.

6. W **przyborniku** rozwiń **wszystkie Windows Forms** i przeciągnij kontrolkę **etykieta** do formularza.

7. W projektancie kliknij kontrolkę etykieta.

8. W oknie **Właściwości** Zmień właściwość **Text** w obszarze **wygląd** na następujący:

    Aplikacja, którą chcesz zainstalować, sprawdza dostępność najnowszych aktualizacji w sieci Web. Klikając pozycję "Zgadzam się", upoważniasz aplikację do automatycznego sprawdzania i instalowania aktualizacji z Internetu.

9. W **przyborniku** przeciągnij formant **CheckBox** do środka formularza.

10. W oknie **Właściwości** Zmień właściwość **Text** w obszarze **Układ** na **zgadzam** się.

11. W **przyborniku** przeciągnij kontrolkę **Button** do lewego dolnego rogu formularza.

12. W oknie **Właściwości** Zmień właściwość **Text** w obszarze **Układ** , aby **kontynuował**.

13. W oknie **Właściwości** Zmień właściwość **(nazwa)** w obszarze **projekt** na **ProceedButton**.

14. W **przyborniku** przeciągnij kontrolkę **Button** do prawej dolnej krawędzi formularza.

15. W oknie **Właściwości** Zmień właściwość **Text** w obszarze **Układ** na **Anuluj**.

16. W oknie **Właściwości** Zmień właściwość **(nazwa)** w obszarze **projekt** na **CancelButton**.

17. W projektancie kliknij dwukrotnie pole wyboru **zgadzam** się, aby wygenerować program obsługi zdarzeń CheckedChanged.

18. W pliku kodu Form1 Dodaj następujący kod dla programu obsługi zdarzeń CheckedChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet1":::

19. Zaktualizuj konstruktora klasy, aby domyślnie wyłączyć przycisk " **Wykonaj** ".

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet6":::

20. W pliku kodu Form1 Dodaj następujący kod dla zmiennej logicznej, aby śledzić, czy użytkownik końcowy wyraził zgodę na aktualizacje w trybie online.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet3":::

21. W projektancie kliknij dwukrotnie przycisk " **Wykonaj** ", aby wygenerować procedurę obsługi zdarzeń kliknięcia.

22. W pliku kodu Form1 Dodaj następujący kod do programu obsługi zdarzeń kliknięcia dla przycisku **przechodzenia** .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet2":::


23. W projektancie kliknij dwukrotnie przycisk **Anuluj** , aby wygenerować procedurę obsługi zdarzeń kliknięcia.

24. W pliku kodu Form1 Dodaj następujący kod dla programu obsługi zdarzeń kliknięcia dla przycisku **Anuluj** .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet4":::

25. Zaktualizuj aplikację w celu zwrócenia błędu, jeśli użytkownik końcowy nie wyraża zgody na aktualizacje w trybie online.

     Tylko dla Visual Basic deweloperów:

    1. W **Eksplorator rozwiązań** kliknij pozycję **ConsentDialog**.

    2. W menu **projekt** kliknij polecenie **Dodaj moduł**, a następnie kliknij przycisk **Dodaj**.

    3. W pliku kodu *Module1. vb* Dodaj następujący kod.

       :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb" id="Snippet7":::

    4. W menu **projekt** kliknij polecenie **Właściwości ConsentDialog**, a następnie kliknij kartę **aplikacja** .

    5. Usuń zaznaczenie pola wyboru **Włącz platformę aplikacji**.

    6. W menu rozwijanym **obiekt startowy** wybierz pozycję **Module1**.

       > [!NOTE]
       > Wyłączenie struktury aplikacji powoduje wyłączenie funkcji takich jak style wizualne systemu Windows XP, zdarzenia aplikacji, ekran powitalny, aplikacja o pojedynczym wystąpieniu i wiele więcej. Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Tylko dla deweloperów Visual C#:

       Otwórz plik kodu *programu program. cs* i Dodaj następujący kod.

       :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs" id="Snippet5":::

26. W menu **kompilacja** kliknij pozycję **BuildSolution**.

## <a name="create-the-custom-bootstrapper-package"></a>Tworzenie niestandardowego pakietu programu inicjującego
 Aby wyświetlić monit o prywatność dla użytkowników końcowych, można utworzyć niestandardowy pakiet programu inicjującego dla aplikacji okna dialogowego zgody o zgodę na aktualizację i uwzględnić go jako warunek wstępny we wszystkich aplikacjach ClickOnce.

 W tej procedurze pokazano, jak utworzyć niestandardowy pakiet programu inicjującego, tworząc następujące dokumenty:

- Plik manifestu *product.xml* do opisywania zawartości programu inicjującego.

- Plik manifestu *package.xml* , aby wyświetlić listę aspektów specyficznych dla lokalizacji pakietu, takich jak ciągi i postanowienia licencyjne dotyczące oprogramowania.

- Dokument dotyczący postanowień licencyjnych dotyczących oprogramowania.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Krok 1. Aby utworzyć katalog programu inicjującego

1. Utwórz katalog o nazwie **UpdateConsentDialog** w *%ProgramFiles%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*.

    > [!NOTE]
    > Do utworzenia tego folderu mogą być wymagane uprawnienia administracyjne.

2. W katalogu *UpdateConsentDialog* Utwórz podkatalog o nazwie *pl*.

    > [!NOTE]
    > Utwórz nowy katalog dla każdego ustawienia regionalnego. Na przykład można dodać podkatalogi dla fr i de locale. Te katalogi będą zawierać ciągi francuskie i niemieckie oraz pakiety językowe, w razie potrzeby.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Krok 2. Aby utworzyć plik manifestu product.xml

1. Utwórz plik tekstowy o nazwie *product.xml*.

2. W pliku *product.xml* Dodaj następujący kod XML. Upewnij się, że nie zastąpisz istniejącego kodu XML.

    ```xml
    <Product
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      ProductCode="Microsoft.Sample.EULA">
      <!-- Defines the list of files to be copied on build. -->
      <PackageFiles CopyAllPackageFiles="false">
        <PackageFile Name="ConsentDialog.exe"/>
      </PackageFiles>

      <!-- Defines how to run the Setup package.-->
      <Commands >
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>
          <ExitCodes>
            <ExitCode Value="0" Result="Success" />
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />
            <DefaultExitCode Result="Fail"
              FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
      </Commands>

    </Product>
    ```

3. Zapisz plik w katalogu programu inicjującego UpdateConsentDialog.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Krok 3. Tworzenie pliku manifestu package.xml i postanowień licencyjnych dotyczących oprogramowania

1. Utwórz plik tekstowy o nazwie *package.xml*.

2. W pliku *package.xml* Dodaj następujący kod XML w celu zdefiniowania ustawień regionalnych i uwzględnienia postanowień licencyjnych dotyczących oprogramowania. Upewnij się, że nie zastąpisz istniejącego kodu XML.

    ```xml
    <Package
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      Name="DisplayName"
      Culture="Culture"
      LicenseAgreement="eula.rtf">
      <PackageFiles>
        <PackageFile Name="eula.rtf"/>
      </PackageFiles>

      <!-- Defines a localizable string table for error messages. -->
      <Strings>
        <String Name="DisplayName">Update Consent Dialog</String>
        <String Name="Culture">en</String>
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>
      </Strings>
    </Package>
    ```

3. Zapisz plik w podkatalogu EN w katalogu programu inicjującego UpdateConsentDialog.

4. Utwórz dokument o nazwie *EULA. rtf* dla postanowień licencyjnych dotyczących oprogramowania.

    > [!NOTE]
    > Postanowienia licencyjne dotyczące oprogramowania powinny zawierać informacje o licencjonowaniu, gwarancjach, zobowiązaniach i prawach lokalnych. Te pliki powinny być specyficzne dla ustawień regionalnych, dlatego upewnij się, że plik jest zapisany w formacie obsługującym znaki MBCS lub UNICODE. Zapoznaj się z działem prawnym dotyczącym treści postanowień licencyjnych dotyczących oprogramowania.

5. Zapisz dokument w podkatalogu EN w katalogu programu inicjującego *UpdateConsentDialog* .

6. W razie potrzeby utwórz nowy plik manifestu *package.xml* i nowy dokument *EULA. rtf* dla postanowień licencyjnych dotyczących oprogramowania dla poszczególnych ustawień regionalnych. Na przykład, jeśli utworzono podkatalogi dla fr i de locale, Utwórz oddzielne pliki manifestu package.xml i postanowienia licencyjne dotyczące oprogramowania i Zapisz je w podkatalogach fr i de.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Ustaw aplikację zgody na aktualizację jako warunek wstępny
 W programie Visual Studio można ustawić aplikację zgody na aktualizację jako warunek wstępny.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Aby ustawić zgodę na aktualizację jako warunek wstępny

1. W **Eksplorator rozwiązań** kliknij nazwę aplikacji, którą chcesz wdrożyć.

2. W menu **projekt** kliknij polecenie właściwości *ProjectName* .

3. Kliknij stronę **Publikowanie** , a następnie kliknij pozycję **wymagania wstępne**.

4. Wybierz pozycję **okno dialogowe zgody na aktualizowanie**.

    > [!NOTE]
    > Może być konieczne zamknięcie i ponowne otwarcie programu Visual Studio, aby wyświetlić okno dialogowe zgody na aktualizację w oknie dialogowym wymagania wstępne.

5. Kliknij przycisk **OK**.

## <a name="create-and-test-the-setup-program"></a>Utwórz i przetestuj program instalacyjny
 Po ustawieniu aplikacji zgody na aktualizację jako warunek wstępny można wygenerować Instalatora i program inicjujący dla aplikacji.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Aby utworzyć i przetestować program instalacyjny, nie klikając Zgadzam się

1. W **Eksplorator rozwiązań** kliknij nazwę aplikacji, którą chcesz wdrożyć.

2. W menu **projekt** kliknij polecenie właściwości *ProjectName* .

3. Kliknij stronę **Publikowanie** , a następnie kliknij pozycję **Opublikuj teraz**.

4. Jeśli dane wyjściowe publikowania nie są automatycznie otwierane, przejdź do publikowania danych wyjściowych.

5. Uruchom program *Setup.exe* .

     W programie instalacyjnym zostanie wyświetlona umowa licencyjna na oprogramowanie okno dialogowe zgody na aktualizację.

6. Przeczytaj umowę licencyjną dotyczącą oprogramowania, a następnie kliknij przycisk **Akceptuj**.

     Zostanie wyświetlona aplikacja okno dialogowe zgody na aktualizację, która zawiera następujący tekst: aplikacja, którą chcesz zainstalować, sprawdza, czy są dostępne najnowsze aktualizacje w sieci Web. Klikając przycisk Zgadzam się, autoryzujesz aplikację, aby automatycznie sprawdzać dostępność aktualizacji w Internecie.

7. Zamknij aplikację lub kliknij przycisk Anuluj.

     Aplikacja wyświetla błąd: Wystąpił błąd podczas instalowania składników systemowych dla programu *ApplicationName*. Instalator nie może kontynuować pracy, dopóki wszystkie składniki systemowe nie zostaną pomyślnie zainstalowane.

8. Kliknij przycisk Szczegóły, aby wyświetlić następujący komunikat o błędzie: nie można zainstalować okna dialogowego zgody o zgodę na aktualizację składnika. komunikat o błędzie: "Umowa dotycząca aktualizacji automatycznych nie została zaakceptowana". Nie można zainstalować następujących składników:-aktualizowanie okna dialogowego zgody

9. Kliknij przycisk **Zamknij**.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Aby utworzyć i przetestować program instalacyjny, klikając przycisk Zgadzam się

1. W **Eksplorator rozwiązań** kliknij nazwę aplikacji, którą chcesz wdrożyć.

2. W menu **projekt** kliknij polecenie właściwości *ProjectName* .

3. Kliknij stronę **Publikowanie** , a następnie kliknij pozycję **Opublikuj teraz**.

4. Jeśli dane wyjściowe publikowania nie są automatycznie otwierane, przejdź do publikowania danych wyjściowych.

5. Uruchom program *Setup.exe* .

     W programie instalacyjnym zostanie wyświetlona umowa licencyjna na oprogramowanie okno dialogowe zgody na aktualizację.

6. Przeczytaj umowę licencyjną dotyczącą oprogramowania, a następnie kliknij przycisk **Akceptuj**.

     Zostanie wyświetlona aplikacja okno dialogowe zgody na aktualizację, która zawiera następujący tekst: aplikacja, którą chcesz zainstalować, sprawdza, czy są dostępne najnowsze aktualizacje w sieci Web. Klikając przycisk Zgadzam się, autoryzujesz aplikację, aby automatycznie sprawdzać dostępność aktualizacji w Internecie.

7. Kliknij przycisk **zgadzam** się, a następnie kliknij przycisk **Zastosuj**.

     Instalacja aplikacji rozpocznie się.

8. Jeśli zostanie wyświetlone okno dialogowe Instalacja aplikacji, kliknij przycisk **Instaluj**.

## <a name="see-also"></a>Zobacz też
- [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
- [Tworzenie niestandardowych pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)
- [Instrukcje: tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md)
- [Instrukcje: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)