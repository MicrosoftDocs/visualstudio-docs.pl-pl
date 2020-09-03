---
title: Tworzenie niestandardowych projektów z obsługą wersji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 0b29728cffc962b5d09a5adc45f8cac2093b020a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825687"
---
# <a name="making-custom-projects-version-aware"></a>Tworzenie niestandardowych projektów z obsługą wersji
W niestandardowym systemie projektu można zezwolić na załadowanie projektów tego typu w wielu wersjach programu Visual Studio. Można również uniemożliwić ładowanie projektów tego typu we wcześniejszej wersji programu Visual Studio. Możesz również włączyć ten projekt, aby identyfikować go do nowszej wersji w przypadku, gdy projekt wymaga naprawy, konwersji lub wycofania.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Zezwalanie na ładowanie projektów w wielu wersjach  
 Większość projektów, które zostały utworzone w programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1 lub nowszym, można modyfikować w wielu wersjach.  
  
 Przed załadowaniem projektu program Visual Studio wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> metodę w celu ustalenia, czy projekt może zostać uaktualniony. Jeśli projekt można uaktualnić, `UpgradeProject_CheckOnly` Metoda ustawia flagę, która powoduje późniejsze wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody w celu uaktualnienia projektu. Ponieważ nie można uaktualnić niezgodnych projektów, `UpgradeProject_CheckOnly` należy najpierw sprawdzić zgodność projektu, zgodnie z opisem w poprzedniej sekcji.  
  
 Jesteś autorem systemu projektu, zaimplementuj `UpgradeProject_CheckOnly` (z `IVsProjectUpgradeViaFactory4` interfejsu), aby zapewnić użytkownikom systemu projektu kontrolę uaktualnienia. Gdy użytkownicy otwierają projekt, ta metoda jest wywoływana w celu ustalenia, czy projekt musi zostać naprawione przed załadowaniem. Możliwe wymagania dotyczące uaktualniania są wyliczane w programie `VSPUVF_REPAIRFLAGS` i obejmują następujące możliwości:  
  
1. `SPUVF_PROJECT_NOREPAIR`: Nie wymaga naprawy.  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: Sprawia, że projekt jest zgodny ze starszą wersją bez problemów, które mogą wystąpić w poprzednich wersjach produktu.  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: Powoduje, że projekt jest zgodny z poprzednimi wersjami, ale z pewnym ryzykiem problemów, które mogły wystąpić w poprzednich wersjach produktu. Na przykład projekt nie będzie zgodny, jeśli zależy od różnych wersji zestawu SDK.  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE`: Sprawia, że projekt jest niezgodny ze starszą wersją.  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: Wskazuje, że bieżąca wersja nie obsługuje tego projektu.  
  
6. `VSPUVF_PROJECT_DEPRECATED`: Wskazuje, że ten projekt nie jest już obsługiwany.  
  
> [!NOTE]
> Aby uniknąć nieporozumień, nie łącz flag uaktualniania po ich ustawieniu. Na przykład nie należy tworzyć niejednoznacznego stanu uaktualnienia, takiego jak `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED` .  
  
 Typy projektu mogą implementować funkcję `UpgradeProjectFlavor_CheckOnly` z `IVsProjectFlavorUpgradeViaFactory2` interfejsu. Aby ta funkcja działała, `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` implementacja wymieniona wcześniej musi ją wywołać. To wywołanie jest już zaimplementowane w podstawowym systemie projektu Visual Basic lub C#. Efekt tej funkcji umożliwia określenie wersji projektu, aby określić wymagania dotyczące uaktualniania projektu, a także to, co ustalił system projektu podstawowego. Okno dialogowe zgodność zawiera najważniejsze dwa wymagania.  
  
 Gdy program Visual Studio wykonuje sprawdzanie uaktualnienia, zamiast wartości NULL, tak jak w poprzednich wersjach programu Visual Studio, zapewnia rejestratora. Rejestrator włącza systemy i wersje projektu, aby zapewnić dodatkowe informacje, które mogą pomóc w zrozumieniu natury zmian, które są potrzebne do poprawnego załadowania starszych projektów. Zalecamy używanie rejestratora, aby uzyskać więcej informacji zamiast korzystać z okien dialogowych. Więcej informacji można znaleźć w dalszej [części tego tematu](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) .  
  
 W przypadku implementacji zarządzanych interfejsy uaktualniania projektu są dostępne w zestawie Microsoft.VisualStudio.Shell.Interop.11.0.dll międzyoperacyjnych.  
  
 `UpgradeProject`Metoda może określić, czy wprowadzone zmiany uniemożliwiają załadowanie projektu w poprzedniej wersji programu Visual Studio. Jeśli tak, metoda oznacza projekt jako niezgodny. Aby zrozumieć, jak projekt jest oznaczony jako niezgodny, zobacz [oznaczanie projektu jako niezgodnego](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) wcześniej w tym temacie. Zaleca się, aby po wyświetleniu tego okna dialogowego oznaczyć projekt jako niezgodny przez wywołanie metody `IVsAppCompat.BreakAssetCompatibility` bezpośrednio, zamiast wywołania metody, `IVsAppCompat.AskForUserConsentToBreakAssetCompat` ponieważ okno dialogowe nie musi być dwa razy.  
  
 Oto przykład, aby ułatwić podsumowanie środowiska użytkownika dotyczącego zgodności. Jeśli projekt został utworzony we wcześniejszej wersji, a bieżąca wersja ustali, że wymagane jest uaktualnienie, program Visual Studio wyświetli okno dialogowe z poproszeniem użytkownika o zgodę na wprowadzenie zmian. Jeśli użytkownik wyrazi zgodę, projekt zostanie zmodyfikowany, a następnie załadowany. Jeśli rozwiązanie zostanie zamknięte i ponownie otwarte w starszej wersji, projekt jednokierunkowy nie będzie zgodny i nie został załadowany. Jeśli projekt wymagał tylko naprawy (zamiast uaktualnienia), naprawiony projekt nadal zostanie otwarty w obu wersjach.  
  
## <a name="marking-a-project-as-incompatible"></a><a name="BKMK_Incompat"></a> Oznaczanie projektu jako niezgodnego  
 Można oznaczyć projekt jako niezgodny ze starszymi wersjami programu Visual Studio.  Załóżmy na przykład, że tworzysz projekt, który używa funkcji .NET Framework 4,5. Ponieważ tego projektu nie można skompilować [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , można oznaczyć go jako niezgodny, aby zapobiec próbie załadowania tej wersji.  
  
 Składnik, który dodaje niezgodną funkcję, jest odpowiedzialny za oznaczenie projektu jako niezgodnego. Składnik musi mieć dostęp do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu, który reprezentuje interesujące projekty.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Aby oznaczyć projekt jako niezgodny  
  
1. W składniku Pobierz `IVsAppCompat` interfejs z globalnej usługi SVsSolution.  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2. W składniku Wywołaj `IVsAppCompat.AskForUserConsentToBreakAssetCompat` i przekaż go do tablicy `IVsHierarchy` interfejsów, które reprezentują projekty zainteresowania.  
  
     Ta metoda ma następujący podpis:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     W przypadku zaimplementowania tego kodu zostanie wyświetlone okno dialogowe zgodność projektu. W oknie dialogowym zostanie wyświetlony monit z pytaniem o zezwolenie użytkownikowi na oznaczenie wszystkich określonych projektów jako niezgodnych. Jeśli użytkownik wyrazi zgodę, `AskForUserConsentToBreakAssetCompat` zwraca `S_OK` ; w przeciwnym razie `AskForUserConsentToBreakAssetCompat` zwraca `OLE_E_PROMPTSAVECANCELLED` .  
  
    > [!WARNING]
    > W większości typowych scenariuszy `IVsHierarchy` Tablica będzie zawierać tylko jeden element.  
  
3. Jeśli `AskForUserConsentToBreakAssetCompat` zwraca `S_OK` , składnik powoduje lub akceptuje zmiany, które przerywają zgodność.  
  
4. W składniku Wywołaj `IVsAppCompat.BreakAssetCompatibility` metodę dla każdego projektu, który ma zostać oznaczony jako niezgodny. Składnik może ustawić wartość parametru `lpszMinimumVersion` na określoną minimalną wersję, a nie z programu Visual Studio wyszukać bieżący ciąg wersji w rejestrze. Takie podejście minimalizuje ryzyko naruszenia przez składnik wyższej wartości w przyszłości, w zależności od tego, co znajduje się w rejestrze w tym czasie. Jeśli ta wyższa wartość została ustawiona, program Visual Studio nie może otworzyć projektu.  
  
     Ta metoda ma następujący podpis:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Jeśli składnik `lpszMinimumVersion` ma wartość null, `BreakAssetCompatibility` Metoda wywołuje `IVsAppCompat.GetCurrentDesignTimeCompatVersion` metodę w celu uzyskania ciągu reprezentującego bieżącą wersję programu Visual Studio.  
  
     Ta metoda ma następujący podpis:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Metoda BreakAssetCompatibility następnie wywołuje metodę, `IVsHierarchy.SetProperty` Aby ustawić `VSHPROPID_MinimumDesignTimeCompatVersion` Właściwość root na wartość ciągu wersji uzyskanego w poprzednim kroku.  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
> Musisz zaimplementować właściwość, `VSHPROPID_MinimumDesignTimeCompatVersion` Aby oznaczyć projekt jako zgodny lub niezgodny. Na przykład jeśli system projektu używa pliku projektu MSBuild, należy dodać do pliku projektu `<MinimumVisualStudioVersion>` Właściwość kompilacji, która ma wartość równą odpowiadającej `VSHPROPID_MinimumDesignTimeCompatVersion` wartości właściwości.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Wykrywanie, czy projekt jest niezgodny  
 Nie można załadować projektu, który jest niezgodny z bieżącą wersją programu Visual Studio. Ponadto nie można uaktualnić ani naprawić projektu, który jest niezgodny. W związku z tym projekt musi być sprawdzony pod kątem zgodności dwa razy: najpierw, gdy jest brany pod uwagę w celu uaktualnienia lub naprawy, a drugi przed załadowaniem.  
  
 Aby włączyć wykrywanie niezgodności projektu, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metody i. Jeśli projekt jest niezgodny, `UpgradeProject_CheckOnly` musi zwrócić kod sukcesu `VS_S_INCOMPATIBLEPROJECT` i `CreateProject` musi zwrócić kod błędu `VS_E_INCOMPATIBLEPROJECT` . W przypadku projektów z niektórymi wersjami należy zaimplementować `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` zamiast `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` .  
  
 System projektu jest określany jako zaprojektowany w przypadku, gdy ma oparty na nim element Web, pakiet Office (VSTO), program Silverlight lub inny typ projektu. Starsze systemy projektu, które już implementują `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` i są obsługiwane systemy projektów, które już implementują `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` . Starsza wersja programu `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` ma następującą sygnaturę implementacji:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Jeśli ta metoda `pUpgradeRequired` jest ustawiona na wartość true i Returns `S_OK` , wynik jest traktowany jako "upgrade" i tak, jakby Metoda ustawił flagę uaktualnienia na wartość `VSPUVF_PROJECT_ONEWAYUPGRADE` , która jest opisana w dalszej części tego tematu. Następujące zwracane wartości są obsługiwane za pomocą tej starszej metody, ale tylko wtedy `pUpgradeRequired` , gdy jest ustawiona na true:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Ta wartość zwracana tłumaczy `pUpgradeRequired` wartość na true jako odpowiednik `VSPUVF_PROJECT_SAFEREPAIR` , który jest opisany w dalszej części tego tematu.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Ta wartość zwracana tłumaczy `pUpgradeRequired` wartość na true jako odpowiednik `VSPUVF_PROJECT_UNSAFEREPAIR` , który jest opisany w dalszej części tego tematu.  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Ta wartość zwracana tłumaczy `pUpgradeRequired` wartość na true jako odpowiednik `VSPUVF_PROJECT_ONEWAYUPGRADE` , który jest opisany w dalszej części tego tematu.  
  
   Nowe implementacje w systemach `IVsProjectUpgradeViaFactory4` i `IVsProjectFlavorUpgradeViaFactory2` umożliwiają określanie typu migracji dokładniej.  
  
> [!NOTE]
> Można przechować wynik kontroli zgodności przez `UpgradeProject_CheckOnly` metodę, aby można było go również użyć w przypadku kolejnego wywołania do `CreateProject` .  
  
 Na przykład, jeśli `UpgradeProject_CheckOnly` metody i `CreateProject` , które są zapisywana dla [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] systemu projektu z dodatkiem SP1, przeanalizują plik projektu i stwierdzą, że `<MinimumVisualStudioVersion>` właściwość kompilacja to "11,0", program Visual Studio 2010 z dodatkiem SP1 nie będzie ładować projektu. Ponadto **Nawigator rozwiązań** wskaże, że projekt jest "niezgodny" i nie ładuje go.  
  
## <a name="the-upgrade-logger"></a><a name="BKMK_UpgradeLogger"></a> Rejestrator uaktualnienia  
 Wywołanie `IVsProjectUpgradeViaFactory::UpgradeProject` zawiera `IVsUpgradeLogger` rejestratora, którego systemy i typy projektów powinny być używane do zapewnienia szczegółowego śledzenia uaktualniania na potrzeby rozwiązywania problemów. Jeśli zostanie zarejestrowane ostrzeżenie lub błąd, program Visual Studio wyświetli raport dotyczący uaktualniania.  
  
 Podczas zapisywania do rejestratora uaktualniania należy wziąć pod uwagę następujące wytyczne:  
  
- Program Visual Studio wywoła opróżnianie po zakończeniu uaktualniania wszystkich projektów. Nie wywołuj go w systemie projektu.  
  
- Funkcja LogMessage ma następujące ErrorLevel:  
  
  - 0 dotyczy wszystkich informacji, które mają być śledzone.  

  - 1 to ostrzeżenie.  

  - 2 dotyczy błędu  

  - 3 jest przeznaczony dla programu formatującego raportu. Po uaktualnieniu projektu należy ponownie zarejestrować słowo "skonwertowane" i nie lokalizować tego słowa.  
  
- Jeśli projekt nie wymaga naprawy ani uaktualnienia, program Visual Studio wygeneruje plik dziennika tylko wtedy, gdy system projektu zarejestrował ostrzeżenie lub wystąpił błąd podczas UpgradeProject_CheckOnly lub UpgradeProjectFlavor_CheckOnly metod.
