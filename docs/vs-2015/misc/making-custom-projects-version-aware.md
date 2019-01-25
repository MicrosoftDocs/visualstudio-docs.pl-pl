---
title: Tworzenie niestandardowych projektów rozpoznający wersje | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5b2cfb51ad13ed28e1f021b19b52153bf4c09f62
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768043"
---
# <a name="making-custom-projects-version-aware"></a>Tworzenie niestandardowych projektów rozpoznający wersje
W systemie niestandardowego projektu można zezwolić projektów tego typu są ładowane w wielu wersjach programu Visual Studio. Projekty tego typu mogą również uniemożliwić ładowanie we wcześniejszej wersji programu Visual Studio. Można również włączyć tego projektu w celu zidentyfikowania się względem nowszej wersji. w przypadku, gdy projekt wymaga naprawy, konwersji i wycofywania.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Zezwolenie na obciążenia projektów w różnych wersjach  
 Można modyfikować większość projektów, które zostały utworzone w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1 lub nowszej, aby pracować w wielu wersji.  
  
 Przed załadowaniem projektu programu Visual Studio wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> metodę pozwala ustalić, czy projekt może zostać uaktualniony. Jeśli projekt może zostać uaktualniony, `UpgradeProject_CheckOnly` metoda ustawia flagę powodującą nowszych wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodę, aby uaktualnić projekt. Ponieważ nie można uaktualnić niezgodne projektów, `UpgradeProject_CheckOnly` musisz najpierw sprawdzić zgodność projektu, zgodnie z opisem we wcześniejszej sekcji.  
  
 Autor system projektu, implementowania `UpgradeProject_CheckOnly` (z `IVsProjectUpgradeViaFactory4` interfejsu) umożliwiają zapewnienie użytkownikom systemu projektu sprawdzenie uaktualnienia. Po otwarciu projektu, ta metoda jest wywoływana w celu ustalenia, czy projekt musi zostać naprawiony, przed ich załadowaniem. Możliwe wymagania dotyczące uaktualnienia znajduje się w `VSPUVF_REPAIRFLAGS`, i obejmują one następujące możliwości:  
  
1.  `SPUVF_PROJECT_NOREPAIR`: Wymaga nie naprawy.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: Sprawia, że projekt niezgodny z wcześniejszej wersji bez problemów, które mogą wystąpić natrafić, za pomocą poprzedniej wersji produktu.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: Sprawia, że projekt wstecznie zgodny, ale z pewne ryzyko problemów, które można spotkać w poprzednich wersjach produktu. Na przykład projektu nie będą zgodne, jeśli zależy od różnych wersji zestawu SDK.  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: Sprawia, że projekt niezgodny z wcześniejszą wersją.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: Wskazuje, że bieżąca wersja nie obsługuje tego projektu.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: Wskazuje, że ten projekt nie jest już obsługiwana.  
  
> [!NOTE]
>  Aby uniknąć nieporozumień, nie łączyć flagi uaktualniania po ich wprowadzeniu. Na przykład nie należy tworzyć niejednoznaczne stan uaktualnienia takich jak `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Podtypy projektów może wdrożyć funkcję `UpgradeProjectFlavor_CheckOnly` z `IVsProjectFlavorUpgradeViaFactory2` interfejsu. Aby ta funkcja działa, `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` implementacji, o których wspomniano wcześniej, należy wywołać go. To wywołanie jest już zaimplementowany w systemie projektu podstawowego języka Visual Basic lub C#. Wpływ ta funkcja umożliwia podtypy projektów można również określić wymagania dotyczące uaktualnienia projektu, oprócz systemu podstawowego projektu, co stwierdził. Okno dialogowe zgodności zawiera najpoważniejsze z poniższych wymagań.  
  
 Gdy program Visual Studio wykona sprawdzenie uaktualnienia, zapewnia rejestratora zamiast wartości NULL, tak jak w poprzednich wersjach programu Visual Studio. Rejestrator umożliwia systemy projektu i wersjach w odpowiedzi zawierają dodatkowe informacje, które mogą ułatwić zrozumienie natury zmiany, które są niezbędne do swoich projektów starsze ładują się prawidłowo. Zalecamy użycie rejestratora zawierać dodatkowe informacje, zamiast korzystać z okien dialogowych. Aby uzyskać więcej informacji, zobacz [rejestratora uaktualnienia](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) w dalszej części tego tematu.  
  
 Dla implementacji zarządzane interfejsy uaktualnienia projektu są dostępne w Microsoft.VisualStudio.Shell.Interop.11.0.dll zestawu międzyoperacyjnego.  
  
 `UpgradeProject` Metoda można określić, czy zmiany to sprawia, że może uniemożliwić projektu ładowania w poprzedniej wersji programu Visual Studio. Jeśli tak, metoda oznacza projekt jako niezgodne. Aby dowiedzieć się, jak projekt jest oznaczona jako niezgodna, zobacz [oznaczanie projektu jako niezgodny](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) we wcześniejszej części tego tematu. Zaleca się, że po wyświetleniu tego okna dialogowego, oznaczasz projektu jako niezgodne przez wywołanie metody `IVsAppCompat.BreakAssetCompatibility` bezpośrednio, bez wywoływania pierwszy `IVsAppCompat.AskForUserConsentToBreakAssetCompat` metody ponieważ okno dialogowe nie musi ono być widoczne dwa razy.  
  
 Oto przykład ułatwiające podsumowanie zgodności środowisko użytkownika. Jeżeli projekt został utworzony we wcześniejszej wersji, a bieżąca wersja Określa, że wymagane jest uaktualnienie, Visual Studio Wyświetla okno dialogowe, aby poprosić użytkownika o zgodę wprowadzić zmiany. Za zgodą użytkownika, projekt jest zmodyfikowany i następnie ładowany. Jeśli rozwiązanie jest następnie zamknięty i ponownie otworzyć w starszej wersji, uaktualnić way jeden projekt będzie niezgodne i nie załadowany. W razie projekt miał tylko naprawy (a nie uaktualnienie) naprawionych projektu nadal otworzy się w obu wersjach.  
  
##  <a name="BKMK_Incompat"></a> Oznaczanie projektu jako niezgodne  
 Możesz oznaczyć projektu jako niezgodne z wcześniejszymi wersjami programu Visual Studio.  Na przykład załóżmy, że utworzono projekt, który używa funkcji .NET Framework 4.5. Ponieważ ten projekt nie może być wbudowane [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], oznacz ją jako niezgodne, aby zapobiec próby załadowania go w tej wersji.  
  
 Składnik, który dodaje funkcję niezgodne jest odpowiedzialny za oznaczenie projektu jako niezgodne. Składnik musi mieć dostęp do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejs, który reprezentuje projektów będących przedmiotem zainteresowania.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Aby oznaczyć projektu jako niezgodne  
  
1.  W składniku `IVsAppCompat` interfejsu usługi globalne SVsSolution.  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  W składniku, należy wywołać `IVsAppCompat.AskForUserConsentToBreakAssetCompat`i przekaż go tablicę `IVsHierarchy` interfejsy, które reprezentują projektów będących przedmiotem zainteresowania.  
  
     Ta metoda ma następujący podpis:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     W przypadku zastosowania tego kodu, pojawi się okno dialogowe zgodność projektu. Zostanie okno dialogowe prosi użytkownika o zezwolenie na oznaczenie wszystkich określonych projektów jako niezgodne. Za zgodą użytkownika, `AskForUserConsentToBreakAssetCompat` zwraca `S_OK`; w przeciwnym razie `AskForUserConsentToBreakAssetCompat` zwraca `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  W najbardziej typowych scenariuszy `IVsHierarchy` tablicy będzie zawierać tylko jeden element.  
  
3.  Jeśli `AskForUserConsentToBreakAssetCompat` zwraca `S_OK`, składnik sprawia, że lub akceptuje zmiany naruszające zgodności.  
  
4.  W składniku, należy wywołać `IVsAppCompat.BreakAssetCompatibility` metodę dla każdego projektu, który ma zostać oznaczone jako niezgodne. Ten składnik można ustawić wartości parametru `lpszMinimumVersion` do określonej minimalnej wersji zamiast programu Visual Studio, Wyszukaj bieżący ciąg wersji w rejestrze. To podejście minimalizuje ryzyko przypadkowo ustawienie wyższej wartości w przyszłości na podstawie co znajduje się w rejestrze w tym czasie składnika. Jeśli ustawiono tej wartości wyższej, Visual Studio nie można otworzyć projektu.  
  
     Ta metoda ma następujący podpis:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Jeśli składnik ustawia `lpszMinimumVersion` na wartość NULL, `BreakAssetCompatibility` wywołania metody `IVsAppCompat.GetCurrentDesignTimeCompatVersion` metodę, aby uzyskać ciąg reprezentujący bieżącą wersję programu Visual Studio.  
  
     Ta metoda ma następujący podpis:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Następnie wywołuje metodę BreakAssetCompatibility `IVsHierarchy.SetProperty` metodę, aby ustawić katalogu głównego `VSHPROPID_MinimumDesignTimeCompatVersion` właściwości do wartości ciągu wersji, uzyskanych w poprzednim kroku.  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Musisz zaimplementować `VSHPROPID_MinimumDesignTimeCompatVersion` właściwości, aby oznaczyć projektu jako zgodne lub niezgodne. Na przykład, jeśli system projektu używa pliku projektu programu MSBuild, Dodaj do pliku projektu `<MinimumVisualStudioVersion>` kompilacji właściwość, która ma wartość równą do odpowiednich `VSHPROPID_MinimumDesignTimeCompatVersion` wartości właściwości.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Wykrywanie czy projekt jest niezgodny  
 Projekt, który jest niezgodny z bieżącą wersją programu Visual Studio muszą być przechowywane z ładowania. Ponadto projekt, który jest niezgodny nie można uaktualnić lub naprawy. W związku z tym, projekt musi być zaznaczone dla zgodności dwa razy: pierwszy, gdy jest rozważane dla uaktualnienie lub naprawy, a drugie, przed jego załadowaniu.  
  
 Aby włączyć wykrywanie niezgodności projektu, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metody. Jeśli projekt jest niezgodny, `UpgradeProject_CheckOnly` musi zwracać kod powodzenia `VS_S_INCOMPATIBLEPROJECT`, i `CreateProject` musi zwracać kod błędu: `VS_E_INCOMPATIBLEPROJECT`. Dla odmian projektów, należy zaimplementować `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` zamiast `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 System projektu jest określany do jako flavored, jeśli ma on sieci web, pakietu Office (VSTO), Silverlight lub innych typów projektów, zbudowany na podstawie jej. Starsze systemy projektu, które zawierają już implementację `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` i składni systemy projektu, które zawierają już implementację `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` nadal są obsługiwane. Starszą wersję `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` ma następujący podpis implementacji:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Jeśli ta metoda ustawia `pUpgradeRequired` PRAWDA i zwraca `S_OK`, wynik jest traktowana jako "Uaktualnianie" i tak, jakby metody uaktualniania flagę ustawić na wartość `VSPUVF_PROJECT_ONEWAYUPGRADE`, który jest opisany w dalszej części tego tematu. Następujące zwracają wartości są obsługiwane przy użyciu tego starsza metoda, ale tylko wtedy, gdy `pUpgradeRequired` jest ustawiona na wartość TRUE:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Tłumaczy to wartość zwracana `pUpgradeRequired` wartość true jako odpowiednik `VSPUVF_PROJECT_SAFEREPAIR`, który jest opisany w dalszej części tego tematu.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Tłumaczy to wartość zwracana `pUpgradeRequired` wartość true jako odpowiednik `VSPUVF_PROJECT_UNSAFEREPAIR`, który jest opisany w dalszej części tego tematu  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Tłumaczy to wartość zwracana `pUpgradeRequired` wartość true jako odpowiednik `VSPUVF_PROJECT_ONEWAYUPGRADE`, który jest opisany w dalszej części tego tematu.  
  
   Nowe implementacje w `IVsProjectUpgradeViaFactory4` i `IVsProjectFlavorUpgradeViaFactory2` umożliwić bardziej precyzyjne określanie typu migracji.  
  
> [!NOTE]
>  Może buforować wynik sprawdzania zgodności przez `UpgradeProject_CheckOnly` metodę, tak że można również przez kolejne wywołanie `CreateProject`.  
  
 Na przykład jeśli `UpgradeProject_CheckOnly` i `CreateProject` metody, które zostały napisane dla [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1, system projektu badania pliku projektu i okazać, że `<MinimumVisualStudioVersion>` właściwość kompilacji "11.0", nie można załadować projektu programu Visual Studio 2010 z dodatkiem SP1. Ponadto **Nawigator rozwiązania** wskazują, że projekt jest "niezgodne" i nie można go załadować.  
  
##  <a name="BKMK_UpgradeLogger"></a> Uaktualnianie rejestratora  
 Wywołanie `IVsProjectUpgradeViaFactory::UpgradeProject` zawiera `IVsUpgradeLogger` rejestratora, które systemy projektu i odmian należy używać zapewnienie szczegółowe śledzenie uaktualnienia do rozwiązywania problemów. Jeśli ostrzeżenia lub komunikat o błędzie jest rejestrowany, Visual Studio wyświetla raport o uaktualnieniu.  
  
 Podczas próby uaktualnienia rejestratora zapisu, należy wziąć pod uwagę następujące wytyczne:  
  
-   Program Visual Studio będzie wywoływać opróżniania po wszystkie projekty została zakończona, uaktualnianie. Nie wywołuj go w systemie projektu.  
  
-   Logmessage — funkcja ma następujące ErrorLevels:  
  
    -   Usługa 0 jest wszelkie informacje, które chcesz śledzić.  
  
    -   1 jest ostrzeżenie.  
  
    -   2 dotyczy błąd  
  
    -   dla elementu formatującego raportu jest 3. Po uaktualnieniu projektu dziennika słowo "Konwertowane" raz, a nie zlokalizujesz wyraz.  
  
-   Jeśli projekt nie wymaga żadnych naprawy lub uaktualnienia, program Visual Studio wygeneruje plik dziennika tylko wtedy, gdy system projektu ma zarejestrowane ostrzeżenie lub błąd podczas UpgradeProject_CheckOnly lub UpgradeProjectFlavor_CheckOnly metod.