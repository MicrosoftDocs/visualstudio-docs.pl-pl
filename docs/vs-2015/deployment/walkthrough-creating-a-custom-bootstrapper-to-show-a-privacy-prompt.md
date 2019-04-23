---
title: 'Przewodnik: Tworzenie niestandardowego programu inicjującego wyświetlającego monit zasad ochrony prywatności | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 153773d27d4f27a6987f7984955dde26b187b65e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116520"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Przewodnik: Tworzenie niestandardowego programu inicjującego wyświetlającego monit o prywatności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skonfigurować aplikacji ClickOnce do automatycznego aktualizowania zestawy za pomocą nowszej wersji plików i wersje zestawów stają się dostępne. Aby upewnić się, że klienci wyrazić zgodę na to zachowanie, możesz wyświetlić monit o prywatności do nich. Następnie mogą wybrać, czy można udzielić uprawnienia do aplikacji w celu automatycznej aktualizacji. Jeśli aplikacja nie może być aktualizowane automatycznie, nie jest instalowana.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Tworzenie okna dialogowego zgody aktualizacji  
 Wyświetlenie monitu o prywatności, należy utworzyć aplikację, która prosi czytnik do wyrażenia zgody na automatyczne aktualizacje aplikacji.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Aby utworzyć okno dialogowe zgody  
  
1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2. W **nowy projekt** okno dialogowe, kliknij przycisk **Windows**, a następnie kliknij przycisk **WindowsFormsApplication**.  
  
3. Aby uzyskać **nazwa**, typ **ConsentDialog**, a następnie kliknij przycisk **OK**.  
  
4. W Projektancie kliknij formularz.  
  
5. W **właściwości** oknie zmiany **tekstu** właściwości **okna dialogowego zgody aktualizacji**.  
  
6. W **przybornika**, rozwiń węzeł **wszystkie formularze Windows**, a następnie przeciągnij **etykiety** formantu do formularza.  
  
7. W Projektancie kliknij kontrolkę etykiety.  
  
8. W **właściwości** oknie zmiany **tekstu** właściwości **wygląd** do następującego:  
  
    Sprawdza, czy aplikacji, które zamierzasz zainstalować najnowsze aktualizacje w sieci Web. Klikając "Zgadzam się", możesz zezwolić aplikacji, aby wyszukać i automatycznego instalowania aktualizacji z Internetu.  
  
9. W **przybornika**, przeciągnij **wyboru** kontroli w środku formularza.  
  
10. W **właściwości** oknie zmiany **tekstu** właściwości **układ** do **zgadzam się**.  
  
11. W **przybornika**, przeciągnij **przycisk** kontrolki do lewej dolnej części formularza.  
  
12. W **właściwości** oknie zmiany **tekstu** właściwości **układ** do **Kontynuuj**.  
  
13. W **właściwości** oknie zmiany **(nazwa)** właściwości **projektowania** do **ProceedButton**.  
  
14. W **przybornika**, przeciągnij **przycisk** kontrolki na prawej dolnej części formularza.  
  
15. W **właściwości** oknie zmiany **tekstu** właściwości **układ** do **anulować**.  
  
16. W **właściwości** oknie zmiany **(nazwa)** właściwości **projektowania** do **CancelButton**.  
  
17. W projektancie, kliknij dwukrotnie **zgadzam się** pole wyboru, aby wygenerować procedurę obsługi zdarzenia CheckedChanged.  
  
18. W pliku kodu formularza Form1 Dodaj następujący kod do obsługi zdarzenia CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Zaktualizować konstruktora klasy, aby wyłączyć **Kontynuuj** przycisk domyślny.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. W pliku kodu formularza Form1 Dodaj następujący kod do zmiennej typu Boolean do śledzenia, czy użytkownik końcowy wyraził zgodę na aktualizacje w trybie online.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. W projektancie, kliknij dwukrotnie **Kontynuuj** przycisk, aby wygenerować program obsługi zdarzeń kliknięcie.  
  
22. W pliku kodu formularza Form1, Dodaj następujący kod do obsługi zdarzeń kliknij **Kontynuuj** przycisku.  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. W projektancie, kliknij dwukrotnie **anulować** przycisk, aby wygenerować program obsługi zdarzeń kliknięcie.  
  
24. W pliku kodu formularza Form1, Dodaj następujący kod do obsługi zdarzeń kliknij **anulować** przycisku.  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Aktualizuj aplikację, zostać zwrócony błąd, jeśli użytkownik nie zgadza się na aktualizacje w trybie online.  
  
     Visual Basic tylko dla deweloperów:  
  
    1. W **Eksploratora rozwiązań**, kliknij przycisk **ConsentDialog**.  
  
    2. Na **projektu** menu, kliknij przycisk **Dodawanie modułu**, a następnie kliknij przycisk **Dodaj**.  
  
    3. W pliku kodu Module1.vb Dodaj następujący kod.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. Na **projektu** menu, kliknij przycisk **właściwości ConsentDialog**, a następnie kliknij przycisk **aplikacji** kartę.  
  
    5. Usuń zaznaczenie pola wyboru **struktury aplikacji Włącz**.  
  
    6. W **obiekt początkowy** menu rozwijanego wybierz opcję **Module1**.  
  
       > [!NOTE]
       >  Wyłączenie struktury aplikacji powoduje wyłączenie funkcji, takich jak stylów wizualnych Windows XP, zdarzenia aplikacji, ekran powitalny i aplikacja pojedynczego wystąpienia. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Visual C# tylko dla deweloperów:  
  
       Otwórz plik kodu w pliku Program.cs i Dodaj następujący kod.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. Na **kompilacji** menu, kliknij przycisk **Skompiluj rozwiązanie**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Tworzenie pakietu niestandardowego programu inicjującego  
 Aby wyświetlić wiersz zachowania użytkowników końcowych, można utworzyć niestandardowy pakiet programu inicjującego dla okna dialogowego zgody aktualizacji aplikacji i dołączyć go jako warunek wstępny we wszystkich aplikacjach ClickOnce.  
  
 Ta procedura pokazuje, jak utworzyć niestandardowy pakiet programu inicjującego, tworząc następujące dokumenty:  
  
- Product.xml manifest pliku, aby opisać zawartość program inicjujący.  
  
- Package.xml plik manifestu do listy lokalizacji określonych aspektów pakietu, takich jak ciągi i postanowienia licencyjne dotyczące oprogramowania.  
  
- Dokument postanowienia licencyjne dotyczące oprogramowania.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Krok 1. Można utworzyć katalogu programu inicjującego  
  
1. Utwórz katalog o nazwie **UpdateConsentDialog** w %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Uprawnienia administracyjne, aby utworzyć ten folder może być konieczne.  
  
2. W katalogu UpdateConsentDialog Utwórz podkatalog o nazwie en.  
  
    > [!NOTE]
    >  Utwórz nowy katalog dla poszczególnych ustawień regionalnych. Na przykład można dodać podkatalogów dla ustawień regionalnych fr i "de". Te katalogi zawierałoby ciągi francuskim i niemieckim i pakietów językowych, jeśli to konieczne.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Krok 2. Aby utworzyć plik manifestu product.xml  
  
1. Utwórz plik tekstowy o nazwie `product.xml`.  
  
2. W pliku product.xml Dodaj następujący kod XML. Upewnij się, że nie zastępuj istniejącego kodu XML.  
  
    ```  
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
  
3. Zapisz plik w katalogu program inicjujący UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Krok 3. Aby utworzyć plik manifestu package.xml i postanowienia licencyjne dotyczące oprogramowania  
  
1. Utwórz plik tekstowy o nazwie `package.xml`.  
  
2. W pliku package.xml Dodaj następujący kod XML do definiowania ustawień regionalnych i zawierają postanowienia licencyjne dotyczące oprogramowania. Upewnij się, że nie zastępuj istniejącego kodu XML.  
  
    ```  
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
  
3. Zapisz plik do podkatalogu en w katalogu program inicjujący UpdateConsentDialog.  
  
4. Utwórz dokument o nazwie eula.rtf dla postanowienia licencyjne dotyczące oprogramowania.  
  
    > [!NOTE]
    >  Postanowienia licencyjne dotyczące oprogramowania powinny zawierać informacje dotyczące licencji, gwarancji, zobowiązania i prawa miejscowego. Pliki te powinny być specyficzne dla ustawień regionalnych, dlatego upewnij się, że plik jest zapisywany w formacie, który obsługuje znaki MBCS lub UNICODE. Zapoznaj się z działem prawnym o zawartości postanowienia licencyjne dotyczące oprogramowania.  
  
5. Zapisz dokument w podkatalogu en w katalogu program inicjujący UpdateConsentDialog.  
  
6. Jeśli to konieczne, Utwórz nowy plik manifestu package.xml i nowy dokument eula.rtf dla postanowienia licencyjne dotyczące oprogramowania dla poszczególnych ustawień regionalnych. Na przykład jeśli utworzono podkatalogów dla ustawień regionalnych fr i "de" tworzą pliki manifestu package.xml oddzielnym i postanowień licencyjnych dotyczących oprogramowania i zapisują je do podkatalogów fr i "de".  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Ustawienia aktualizacji aplikacji zgody jako warunek wstępny  
 W programie Visual Studio można ustawić zgody aktualizacji aplikacji jako warunek wstępny.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Aby ustawić aktualizowanie zgody aplikacji jako warunek wstępny  
  
1. W **Eksploratora rozwiązań**, kliknij nazwę aplikacji, którą chcesz wdrożyć.  
  
2. Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
3. Kliknij przycisk **Publikuj** strony, a następnie kliknij przycisk **wymagania wstępne**.  
  
4. Wybierz **aktualizacji dialogowe ze zgodą**.  
  
    > [!NOTE]
    >  Może być konieczne zamknięcie i ponowne otwarcie programu Visual Studio Update zgody okno dialogowe jest wyświetlane w oknie dialogowym wstępnie wymagane składniki.  
  
5. Kliknij przycisk **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Tworzenie i testowanie Program instalacyjny  
 Po aktualizacji zgody aplikacji jest ustawiony jako warunek wstępny, można generować Instalatora i programu inicjującego dla swojej aplikacji.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Aby utworzyć i przetestować program instalacyjny, nie klikając zgadzam się  
  
1. W **Eksploratora rozwiązań**, kliknij nazwę aplikacji, którą chcesz wdrożyć.  
  
2. Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
3. Kliknij przycisk **Publikuj** strony, a następnie kliknij przycisk **Publikuj teraz**.  
  
4. Jeśli dane wyjściowe publikowania nie jest otwierany automatycznie, przejdź do publikowanych danych wyjściowych.  
  
5. Uruchom Setup.exe program.  
  
     Program instalacyjny zawiera umowy licencyjnej okna dialogowego zgody aktualizacji oprogramowania.  
  
6. Przeczytaj umowę licencyjną oprogramowania, a następnie kliknij przycisk **Akceptuj**.  
  
     Okno dialogowe zgody aktualizacji aplikacji pojawi się i pokaże następujący tekst: Sprawdza, czy aplikacji, które zamierzasz zainstalować najnowsze aktualizacje w sieci Web. Klikając zgadzam się, upoważniasz aplikacji, aby sprawdzić, czy są aktualizacje automatyczne w Internecie.  
  
7. Zamknij aplikację, lub przycisk Anuluj.  
  
     Aplikacja zawiera błąd: Wystąpił błąd podczas instalowania składników systemowych dla *ApplicationName*. Instalator nie może kontynuować, dopóki wszystkie składniki systemowe zostały pomyślnie zainstalowane.  
  
8. Kliknij przycisk Szczegóły, aby wyświetlić komunikat o błędzie: Okno dialogowe zgody aktualizacji składników ma nie można zainstalować za pomocą następujący komunikat o błędzie: "Umowy automatyczna aktualizacja nie zostanie zaakceptowany." Nie można zainstalować następujące składniki: — okno dialogowe zgody aktualizacji  
  
9. Kliknij przycisk **Zamknij**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Aby utworzyć i przetestować program instalacyjny, klikając przycisk zgadzam się  
  
1. W **Eksploratora rozwiązań**, kliknij nazwę aplikacji, którą chcesz wdrożyć.  
  
2. Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
3. Kliknij przycisk **Publikuj** strony, a następnie kliknij przycisk **Publikuj teraz**.  
  
4. Jeśli dane wyjściowe publikowania nie jest otwierany automatycznie, przejdź do publikowanych danych wyjściowych.  
  
5. Uruchom Setup.exe program.  
  
     Program instalacyjny zawiera umowy licencyjnej okna dialogowego zgody aktualizacji oprogramowania.  
  
6. Przeczytaj umowę licencyjną oprogramowania, a następnie kliknij przycisk **Akceptuj**.  
  
     Okno dialogowe zgody aktualizacji aplikacji pojawi się i pokaże następujący tekst: Sprawdza, czy aplikacji, które zamierzasz zainstalować najnowsze aktualizacje w sieci Web. Klikając zgadzam się, upoważniasz aplikacji, aby sprawdzić, czy są aktualizacje automatyczne w Internecie.  
  
7. Kliknij przycisk **zgadzam się**, a następnie kliknij przycisk **Kontynuuj**.  
  
     Aby zainstalować uruchamiania aplikacji.  
  
8. Jeśli pojawi się okno dialogowe instalowanie aplikacji, kliknij przycisk **zainstalować**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania wstępne wdrożenia aplikacji](../deployment/application-deployment-prerequisites.md)   
 [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)   
 [Instrukcje: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md)   
 [Instrukcje: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)   
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)
