---
title: Weryfikacja kodu przy użyciu diagramów warstw | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42d7df6e4a4bddc2d3e9bf7ab84375a65a6d2c98
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700652"
---
# <a name="validate-code-with-layer-diagrams"></a>Weryfikacja kodu przy użyciu diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby upewnić się, że kod jest zgodny z projektem, Przeprowadź walidację kodu przy użyciu diagramów warstw w programie Visual Studio. Może to ułatwić:  
  
- Znajdowanie konfliktów między zależnościami w kodzie i na diagramie warstwowym.  
  
- Znajdowanie zależności, na które mogły mieć wpływ proponowane zmiany.  
  
   Na przykład możesz edytować diagram warstwowy, aby pokazać potencjalne zmiany architektury, a następnie walidować kod, aby zobaczyć zależności, na które miały wpływ zmiany.  
  
- Refaktoryzację lub migrację kodu do innego projektu.  
  
   Znajdowanie kodu lub zależności, które wymagają pracy przy przenoszeniu kodu do innej architektury.  
  
  **Wymagania**  
  
- Visual Studio  
  
- Visual Studio na serwerze Team Foundation Build, aby walidować kod automatycznie w programie Team Foundation Build  
  
- Rozwiązanie, które ma projekt modelowania z diagramem warstwowym. Diagram warstwowy musi być połączony z artefaktami w projektach Visual C# .NET lub Visual Basic .NET, które chcesz walidować. Zobacz [tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md).  
  
  Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
  Możesz walidować kod ręcznie z otwartego diagramu warstwowego w Visual Studio lub z wiersza polecenia. Kod możesz również walidować automatycznie podczas uruchamiania lokalnych kompilacji lub programu Team Foundation Build. Zobacz [wideo Channel 9: Projektowanie i Walidacja architektury za pomocą diagramów warstwowych](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
> Jeśli chcesz uruchomić walidację warstwy za pomocą programu Team Foundation Build, należy również zainstalować tę samą wersję programu Visual Studio na serwerze kompilacji.  
  
- [Zobacz, czy element obsługuje walidację](#SupportsValidation)  
  
- [Dołączyć inne projekty, do weryfikacji i zestawy .NET](#IncludeReferences)  
  
- [Ręczna Walidacja kodu](#ValidateManually)  
  
- [Automatycznie Walidacja kodu](#ValidateAuto)  
  
- [Rozwiązywanie problemów z problemy ze sprawdzaniem poprawności warstwy](#TroubleshootingValidation)  
  
- [Omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors)  
  
## <a name="SupportsValidation"></a> Zobacz, czy element obsługuje walidację  
 Możesz połączyć warstwy z witryn sieci Web, dokumentów pakietu Office, plikami ze zwykłym tekstem i plikami w projektach, które są współużytkowane przez wiele aplikacji, ale proces walidacji nie uwzględni je. Błędy walidacji nie będą widoczne w przypadku odwołań do projektów lub zestawów połączonych z oddzielnymi warstwami, jeżeli między tymi warstwami nie ma żadnych zależności. Odwołania te nie są uważane za zależności, chyba że w kodzie wykorzystano te odwołania.  
  
1. Na diagramie warstwowym zaznacz jedną lub więcej warstw, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij **Wyświetl łącza**.  
  
2. W **Eksplorator warstw**, Przyjrzyj się **obsługuje walidację** kolumny. Jeśli wartością jest false, element nie obsługuje walidacji.  
  
## <a name="IncludeReferences"></a> Dołączyć inne projekty, do weryfikacji i zestawy .NET  
 Podczas przeciągania elementów do diagramu warstwowego odwołania do projektów lub odpowiednich zestawów .NET są dodawane automatycznie do **odwołania do warstwy** folderu w projekcie modelowania. Folder ten zawiera odwołania do zestawów i projektów, które są analizowane podczas walidacji. Możesz dołączyć inne projekty i zestawy .NET do walidacji bez ręcznego przeciągania ich do diagramu warstwowego.  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania lub **odwołania do warstwy** folder, a następnie kliknij **Dodaj odwołanie**.  
  
2. W **Dodaj odwołanie** okno dialogowe, zaznacz zestawy lub projekty, a następnie kliknij przycisk **OK**.  
  
## <a name="ValidateManually"></a> Ręczna Walidacja kodu  
 Jeśli masz otwarty diagram warstwowy jest połączony z elementami rozwiązania, możesz uruchomić **weryfikacji** polecenie skrótu z diagramu. Można również użyć wiersza polecenia do uruchomienia **msbuild** polecenia **validatearchitecture** wartość właściwości niestandardowej **True**. Na przykład, po wprowadzeniu dowolnych zmian w kodzie należy regularnie wykonywać walidację warstwy tak, aby można było wcześnie wychwycić konflikty zależności.  
  
#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Aby walidować kod z otwartego diagramu warstwowego  
  
1. Kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij przycisk **sprawdzanie poprawności architektury**.  
  
    > [!NOTE]
    > Domyślnie **Build Action** właściwość warstwy plik diagramu (.layerdiagram) jest ustawiona na **weryfikacji** tak, aby diagram znajduje się w trakcie procesu walidacji.  
  
     **Lista błędów** okna raporty o błędach. Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).  
  
2. Aby wyświetlić źródło każdego błędu, klikaj dwukrotnie poszczególne błędy w **lista błędów** okna.  
  
    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może wyświetlać mapę kodu, zamiast źródła błędu. Dzieje się tak, gdy kod ma zależność z zestawem, która nie jest określona przez diagram warstwowy, lub gdy w kodzie brakuje zależności, która jest określona przez diagram warstwowy. Przejrzyj mapy kodu lub kod w celu określenia, czy powinna istnieć zależność. Aby uzyskać więcej informacji na temat map kodu, zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).  
  
3. Aby zarządzać błędami, zobacz [zarządzanie błędami walidacji](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Aby walidować kod z wiersza polecenia  
  
1. Otwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersza polecenia.  
  
2. Wybierz jedną z następujących opcji:  
  
   - Aby walidować kod dla określonego projektu modelowania w rozwiązaniu, uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującymi niestandardowymi właściwościami.  
  
     ```  
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
     ```  
  
     - lub —  
  
       Przejdź do folderu, który zawiera modelowania projektu (.modelproj) i diagram warstwowy, a następnie uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującymi niestandardowymi właściwościami:  
  
     ```  
     msbuild /p:ValidateArchitecture=true   
     ```  
  
   - Aby walidować kod dla wszystkich projektów modelowania w rozwiązaniu, uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującymi niestandardowymi właściwościami:  
  
     ```  
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
     ```  
  
     - lub —  
  
       Przejdź do folderu rozwiązania, który musi zawierać projekt modelowania zawierający diagram warstwowy, a następnie uruchom [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z następującymi niestandardowymi właściwościami:  
  
     ```  
     msbuild /p:ValidateArchitecture=true  
     ```  
  
     Zostaną wyświetlone wszystkie błędy. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], zobacz [MSBuild](../msbuild/msbuild.md) i [zadanie MSBuild](../msbuild/msbuild-task.md).  
  
   Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).  
  
### <a name="ManageErrors"></a> Zarządzanie błędami walidacji  
 Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Błąd zostanie pominięty, jest dobrym rozwiązaniem do dziennika element roboczy [!INCLUDE[esprfound](../includes/esprfound-md.md)].  
  
> [!WARNING]
> Możesz musi już być podłączony do TFS źródła kodu kontrolki (SCC) można utworzyć lub połączyć elementu roboczego. Jeśli próbujesz nawiązać połączenie z inną SCC TFS, Visual Studio powoduje zamknięcie bieżącego rozwiązania automatycznie. Upewnij się, że jesteś podłączony do odpowiednich SCC przed przystąpieniem do tworzenia lub łącze do elementu roboczego. W kolejnych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone SCC.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Aby utworzyć element roboczy dla błędu walidacji  
  
- W **lista błędów** okna, kliknij błąd prawym przyciskiem myszy, wskaż opcję **Utwórz element pracy**, a następnie kliknij typ elementu roboczego, który chcesz utworzyć.  
  
  Te zadania umożliwiają zarządzanie błędami walidacji w **lista błędów** okna:  
  
|**To**|**Wykonaj następujące kroki**|  
|------------|----------------------------|  
|Pomijanie wybranych błędów podczas walidacji|Kliknij prawym przyciskiem myszy jeden lub kilka zaznaczonych błędów, wskaż opcję **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pomiń błędy**.<br /><br /> Pominięte błędy są wyświetlane jako przekreślone. Przy następnym uruchomieniu walidacji te błędy nie pojawią się.<br /><br /> Pominięte błędy są śledzone w pliku .suppressions związanym z odpowiadającym im plikiem diagramu warstwowego.|  
|Zaprzestanie pomijania wybranych błędów|Kliknij prawym przyciskiem myszy wybrany pominięty błąd lub błędy, wskaż opcję **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Przestań pomijać błędy**.<br /><br /> Wybrane pominięte błędy pojawią się przy następnym uruchomieniu walidacji.|  
|Przywracanie wszystkich pominiętych błędów w **lista błędów** okna|Kliknij prawym przyciskiem myszy w dowolnym miejscu w **lista błędów** okna, wskaż **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|  
|Ukrywanie wszystkich pominiętych błędów w **lista błędów** okna|Kliknij prawym przyciskiem myszy w dowolnym miejscu w **lista błędów** okna, wskaż **zarządzanie błędami walidacji**, a następnie kliknij przycisk **Pokaż wszystkie pominięte błędy**.|  
  
## <a name="ValidateAuto"></a> Automatycznie Walidacja kodu  
 Walidację warstwy możesz wykonać przy każdym uruchomieniu lokalnej kompilacji. Jeśli Twój zespół używa programu Team Foundation Build, możesz wykonać walidację warstwy z bramkowanymi ewidencjonowaniami, którą można określić, tworząc niestandardowe zadanie MSBuild, a następnie używając raportów kompilacji do zbierania błędów walidacji. Aby utworzyć kompilacje z bramkowanym ewidencjonowaniem, zobacz [używać procesu kompilacji ewidencjonowanej warunkowo w celu sprawdzenia poprawności zmian](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Aby walidować kod automatycznie podczas lokalnej kompilacji  
  
- Użyj edytora tekstów, aby otworzyć plik projektu modelowania (.modelproj), a następnie dołącz następującą właściwość:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- lub —  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania, który zawiera diagramy warstwowe, a następnie kliknij przycisk **właściwości**.  
  
2. W **właściwości** okna, Ustaw projekt modelowania **sprawdzanie poprawności architektury** właściwości **True**.  
  
    Dotyczy to projektów modelowania w trakcie procesu walidacji.  
  
3. W **Eksploratora rozwiązań**, kliknij plik diagramu (.layerdiagram) warstwy, którego chcesz używać do sprawdzania poprawności.  
  
4. W **właściwości** okna, upewnij się, że diagram **Build Action** właściwość jest ustawiona na **weryfikacji**.  
  
    Obejmuje to diagram warstwowy w trakcie procesu walidacji.  
  
   Aby zarządzać błędami w oknie Lista błędów, zobacz [zarządzanie błędami walidacji](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Aby walidować kod automatycznie podczas działania programu Team Foundation Build  
  
1. W **Team Explorer**, kliknij dwukrotnie definicję kompilacji, a następnie kliknij przycisk **procesu**.  
  
2. W obszarze **parametrów procesu kompilacji**, rozwiń węzeł **kompilacji**i wpisz następujące polecenie w **argumenty MSBuild** parametru:  
  
    `/p:ValidateArchitecture=true`  
  
   Aby uzyskać więcej informacji na temat błędów sprawdzania poprawności, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors). Aby uzyskać więcej informacji na temat [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], zobacz:  
  
- [Kompiluj aplikację](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
- [Użyj domyślnego szablonu procesu kompilacji](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
- [Modyfikowanie starszej kompilacji oparty na UpgradeTemplate.xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
- [Dostosowywanie szablonu procesu kompilacji](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
- [Monitoruj postęp kompilacji uruchomiony](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
## <a name="TroubleshootingValidation"></a> Rozwiązywanie problemów z problemy ze sprawdzaniem poprawności warstwy  
 W poniższej tabeli opisano problemy związane z walidacją warstwy i ich rozwiązania. Problemy te różnią się od błędów, które wynikają z konfliktów między kodem i projektem. Aby uzyskać więcej informacji na temat tych błędów, zobacz [omówienie i rozwiązywanie błędów walidacji warstwy](#UnderstandingValidationErrors).  
  
|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|  
|---------------|------------------------|--------------------|  
|Błędy walidacji nie występują w oczekiwany sposób.|Walidacja nie działa na diagramach warstwowych, które są kopiowane z innych diagramów warstwowych w Eksploratorze rozwiązań i które są w tym samym projekcie modelowania. Diagramy warstwowe kopiowane w ten sposób zawierają te same odwołania, co oryginalny diagram warstwowe.|Dodaj nowy diagram warstwowy do projektu modelowania.<br /><br /> Skopiuj elementy ze źródłowego diagramu warstwowego do nowego diagramu.|  
  
## <a name="UnderstandingValidationErrors"></a> Zrozumienie i rozwiązywanie błędów walidacji warstwy  
 Podczas walidacji kodu na podstawie diagramu warstwowego błędy walidacji występują, gdy kod jest niezgodny z projektem. Na przykład następujące warunki mogą powodować występowanie błędów walidacji:  
  
- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.  
  
- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.  
  
  Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zadanie to możesz wykonać w sposób iteracyjny.  
  
  W poniższej sekcji opisano składnię, która jest używana w tych błędach, wyjaśniono znaczenie tych błędów i zasugerowano, co można zrobić, aby je rozwiązać lub zarządzać nimi.  
  
|**Składnia**|**Opis**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* jest artefaktem skojarzonym z warstwą na diagramie warstwowym.<br /><br /> *ArtifactTypeN* jest typem *ArtifactN*, takich jak **klasy** lub **metoda**, na przykład:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Metoda)|  
|*NamespaceNameN*|Nazwa przestrzeni nazw.|  
|*LayerNameN*|Nazwa warstwy na diagramie warstwowym.|  
|*DependencyType*|Typ relacji zależności między *Artifact1* i *Artifact2*. Na przykład *Artifact1* ma **wywołania** relacji z *Artifact2*.|  
  
|**Błąd składni**|**Opis błędu**|  
|----------------------|---------------------------|  
|AV0001: Nieprawidłowa zależność: *Artifact1*(*ArtifactType1*) --> *Artifact2*(*ArtifactType2*)<br /><br /> Warstwy: *LayerName1*, *LayerName2* &#124; Dependencies: *DependencyType*|*Artifact1* w *LayerName1* nie powinny mieć zależność *Artifact2* w *LayerName2* ponieważ *LayerName1* nie ma bezpośredniej zależności *LayerName2*.|  
|AV1001: Nieprawidłowy Namespace: *Artefakt*<br /><br /> Warstwa: *LayerName* &#124; wymagane Namespace: *NamespaceName1* &#124; Current Namespace: *NamespaceName2*|*LayerName* wymaga, aby skojarzone artefakty muszą należeć do *NamespaceName1*. *Artefakt* znajduje się w *NamespaceName2*, a nie *NamespaceName1*.|  
|AV1002: Zależy od zabronionej Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Warstwa: *LayerName* &#124; zabronione Namespace: *NamespaceName* &#124; Dependencies: *DependencyType*|*LayerName* wymaga, aby skojarzone artefakty nie zależały od *NamespaceName*. *Artifact1* nie może zależeć od *Artifact2* ponieważ *Artifact2* znajduje się w *NamespaceName*.|  
|AV1003: W zabronionej Namespace: *Artifact*(*ArtifactType*)<br /><br /> Warstwa: *LayerName* &#124; zabronione Namespace: *NamespaceName*|*LayerName* wymaga, aby skojarzone artefakty nie może należeć do *NamespaceName*. *Artefakt* należy do *NamespaceName*.|  
|AV3001: Brakujące łącze: Warstwa "*LayerName*"łączy"*artefaktu*" którego nie można znaleźć. Czy nie brakuje odwołania do zestawu?|*LayerName* łącze do artefaktu, którego nie można odnaleźć. Na przykład, może brakować łącza do klasy, ponieważ w projekcie modelowania brakuje odwołania do zestawu, który zawiera klasę.|  
|AV9001: Analiza architektoniczna znalazła błędy wewnętrzne. Wyniki mogą być niepełne. Aby uzyskać więcej informacji, zobacz szczegółowy dziennik zdarzeń kompilacji lub okno danych wyjściowych.|Zobacz dziennik zdarzeń kompilacji lub okno danych wyjściowych, aby uzyskać więcej szczegółów.|  
  
## <a name="security"></a>Zabezpieczenia  
  
## <a name="see-also"></a>Zobacz też  
 [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
