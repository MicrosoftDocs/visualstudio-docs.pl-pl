---
title: Tworzenie aplikacji ClickOnce z wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dae0859970d5a9a70abb0bed20630348b270a7f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031291"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Tworzenie aplikacji ClickOnce z wiersza polecenia
W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], można kompilować projekty z wiersza polecenia, nawet jeśli są one tworzone w zintegrowanym środowisku programistycznym (IDE). W rzeczywistości, można ponownie utworzyć projekt, który został utworzony za pomocą [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] na innym komputerze, który ma tylko [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zainstalowane. Dzięki temu można odtworzyć za pomocą zautomatyzowanego procesu kompilacji, na przykład w centralnej kompilacji laboratorium lub za pomocą zaawansowane techniki poza zakres tematyczny skompilowanie projektu, sama obsługi skryptów.  
  
## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Użyj programu MSBuild do odtworzenia wdrożenia aplikacji ClickOnce  
 Kiedy wywołujesz /target:publish msbuild w wierszu polecenia, informuje system MSBuild, aby skompilować projekt i Utwórz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w folderze Publikuj. Jest to równoważne z wybraniu **Publikuj** polecenie w IDE.  
  
 To polecenie uruchamia *msbuild.exe*, który jest na ścieżce w środowisku wiersza polecenia programu Visual Studio.  
  
 "target" jest wskaźnikiem do programu MSBuild na temat sposobu przetwarzania polecenia. Kluczowe elementy docelowe są docelowych "kompilacja" i "Publikuj". Element docelowy kompilacji jest to równoważne z wybraniu kompilacji polecenie (lub naciskając klawisz F5) w środowisku IDE. Jeśli chcesz skompilować projekt, można osiągnąć, wpisując `msbuild`. To polecenie działa, ponieważ element docelowy kompilacji jest to domyślny cel dla wszystkich projektów, generowane przez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Oznacza to, że nie trzeba jawnie do określania docelowej kompilacji. W związku z tym, wpisując `msbuild` jest tej samej operacji, ponieważ wpisując `msbuild /target:build`.  
  
 `/target:publish` Polecenie informuje program MSBuild, aby wywołać docelową lokalizację publikacji. Lokalizacja docelowa publikowania zależy od docelowej kompilacji. Oznacza to, że operacja publikowania jest nadzbiorem operacji tworzenia. Na przykład jeśli zmiany zostały wprowadzone do jednego z plików źródłowych języka Visual Basic lub C#, odpowiedni zestaw może automatycznie odbudować przez operację publikowania.  
  
 Aby uzyskać informacje dotyczące generowania pełnego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia za pomocą narzędzia wiersza polecenia Mage.exe, aby utworzyć swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu, zobacz [wskazówki: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Utwórz i skompiluj podstawowych aplikacji ClickOnce za pomocą narzędzia MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Aby utworzyć i opublikować projekt technologii ClickOnce  
  
1. Kliknij przycisk **nowy projekt** z **pliku** menu. **Nowy projekt** pojawi się okno dialogowe.  
  
2. Wybierz **aplikacji Windows** i nadaj mu nazwę `CmdLineDemo`.  
  
3. Z **kompilacji** menu, kliknij przycisk **Publikuj** polecenia.  
  
    Ten krok zapewnia, czy projekt jest prawidłowo skonfigurowane i wygenerować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji.  
  
    Pojawi się Kreator publikacji.  
  
4. W Kreatorze publikowania kliknij **Zakończ**.  
  
    Program Visual Studio zostanie utworzona i wyświetlona domyślna strona internetowa o nazwie *Publish.htm*.  
  
5. Zapisz projekt, a następnie zanotuj lokalizację folderu, w którym są przechowywane.  
  
   Powyższe kroki tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu, który został opublikowany po raz pierwszy. Teraz można odtworzyć kompilacji poza IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Aby odtworzyć kompilacji z wiersza polecenia  
  
1. Zakończ [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2. Z Windows **Start** menu, kliknij przycisk **wszystkie programy**, następnie **programu Microsoft Visual Studio**, następnie **Visual Studio Tools**, następnie **Wiersz polecenia programu visual Studio**. Powinno to otwórz wiersz polecenia w folderze głównym bieżącego użytkownika.  
  
3. W **Visual Studio Command Prompt**, zmień bieżący katalog na lokalizację projektu stworzyłeś właśnie powyżej. Na przykład wpisz `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Aby usunąć istniejące pliki utworzone w "można tworzyć i publikować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu," typ `rmdir /s publish`.  
  
    Ten krok jest opcjonalny, ale zapewnia, że nowe pliki zostały wszystkie utworzone przez kompilację wiersza polecenia.  
  
5. Typ `msbuild /target:publish`.  
  
   Powyższe kroki powoduje wygenerowanie pełnego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji w podfolderze o nazwie projektu **Publikuj**. *CmdLineDemo.application* jest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia. Folder *CmdLineDemo_1.0.0.0* zawiera pliki *CmdLineDemo.exe* i *CmdLineDemo.exe.manifest*, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji. *Setup.exe* jest program inicjujący, która domyślnie jest skonfigurowana do instalowania [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. DotNetFX folder zawiera pakiety redystrybucyjne dla [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Jest to całego zestawu plików, należy wdrożyć aplikację sieci Web lub za pośrednictwem ścieżka UNC lub dysk CD/DVD.  
  
## <a name="publish-properties"></a>Opublikuj właściwości  
 Gdy będziesz publikować aplikację w powyższych procedurach następujące właściwości są wstawiane do pliku projektu, w Kreatorze publikacji. Te właściwości bezpośrednio wpływają na sposób, w jaki [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji są generowane.  
  
 In *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*:  
  
```xml  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Można zastąpić dowolne z tych właściwości w wierszu polecenia, bez zmiany sam plik projektu. Na przykład, następujące utworzy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji bez program inicjujący:  
  
```cmd  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Właściwości publikacji są kontrolowane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z **Publikuj**, **zabezpieczeń**, i **podpisywanie** stron właściwości **Projektant projektu** . Poniżej znajduje się opis właściwości publikacji, wraz ze wskazaniem każdej konfiguracji na różnych stronach właściwości projektanta aplikacji:  
  
- `AssemblyOriginatorKeyFile` Określa plik klucza używany do podpisywania usługi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów aplikacji. Ten sam klucz może również przypisać silną nazwę do zestawów użytkownika. Ta właściwość jest ustawiona na **podpisywanie** strony **projektanta projektu**.  
  
  Następujące właściwości są ustawione na **zabezpieczeń** strony:  
  
- **Włączenie ustawień zabezpieczeń technologii ClickOnce** Określa, czy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] są generowane manifesty. Podczas tworzenia projektu, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generowania manifestu jest domyślnie wyłączona. Kreator automatycznie spowoduje wyłączenie tej flagi na po opublikowaniu po raz pierwszy.  
  
- **TargetZone** określa poziom zaufania, aby być wydane do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji. Możliwe wartości to "Internet", "LocalIntranet" i "Niestandardowe". Internet i LocalIntranet spowoduje, że domyślny zestaw uprawnień, aby być wydane do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji. LocalIntranet jest ustawieniem domyślnym i zasadniczo oznacza pełne zaufanie. Niestandardowe określa tylko uprawnienia, które zostały jawnie określone w podstawowym *app.manifest* plików, które mają być wydane do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji. *App.manifest* plik jest częściowego pliku manifestu, który zawiera tylko definicje informacje zaufania. Jest to plik ukryty, automatycznie dodawane do projektu, podczas konfigurowania uprawnień na **zabezpieczeń** strony.  
  
  Następujące właściwości są ustawione na **Publikuj** strony:  
  
- `PublishUrl` jest to lokalizacja, gdzie aplikacja będzie publikowana w środowisku IDE. Jest wstawiany do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji, jeśli żadna `InstallUrl` lub `UpdateUrl` określono właściwości.  
  
- `ApplicationVersion` Określa wersję [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Jest to numer wersji czterech cyfr. Jeśli ostatnia cyfra jest "*", a następnie `ApplicationRevision` zostanie zastąpiony wartością wstawione do manifestu w czasie kompilacji.  
  
- `ApplicationRevision` Określa poprawkę. Jest to liczba całkowita, która rośnie za każdym razem, gdy opublikujesz w środowisku IDE. Należy zauważyć, że nie jest automatycznie zwiększana do kompilacji wykonywanych w wierszu polecenia.  
  
- `Install` Określa, czy aplikacja jest zainstalowaną aplikacją lub aplikacją Uruchom z sieci Web.  
  
- `InstallUrl` (niewyświetlany) to lokalizacja, w której użytkownicy będą instalować aplikację z. Jeśli zostanie określony, ta wartość jest wbudowany w *setup.exe* programu inicjującego Jeśli `IsWebBootstrapper` właściwość jest włączona. Również jest wstawiany gdy manifestu aplikacji `UpdateUrl` nie zostanie określony.  
  
- `SupportUrl` (niewyświetlany) jest lokalizacja konsolidowana **Dodaj/Usuń programy** okno dialogowe dla zainstalowanej aplikacji.  
  
  Następujące właściwości są ustawiane w **aktualizacje aplikacji** okno dialogowe, dostępne z **Publikuj** strony.  
  
- `UpdateEnabled` Wskazuje, czy aplikacja ma sprawdzać dostępność aktualizacji.  
  
- `UpdateMode` Określa aktualizacje pierwszego planu lub aktualizowane w tle.  
  
- `UpdateInterval` Określa, jak często aplikacja ma sprawdzać dostępność aktualizacji.  
  
- `UpdateIntervalUnits` Określa, czy `UpdateInterval` wartość jest podawana w jednostkach godzin, dni lub tygodni.  
  
- `UpdateUrl` (niewyświetlany) jest to lokalizacja, z której aplikacja będzie otrzymywać aktualizacje. Jeśli zostanie określony, ta wartość jest wstawiany do manifestu aplikacji.  
  
- Następujące właściwości są ustawiane w **opcji publikowania** okno dialogowe, dostępne z **Publikuj** strony.  
  
- `PublisherName` Określa nazwę wydawcy, wyświetlane w wierszu polecenia wyświetlane podczas instalowania lub uruchamiania aplikacji. W przypadku zainstalowanej aplikacji również służy do należy określić nazwę folderu na **Start** menu.  
  
- `ProductName` Określa nazwę produktu, wyświetlane w wierszu polecenia wyświetlane podczas instalowania lub uruchamiania aplikacji. W przypadku zainstalowanej aplikacji również służy do określenia nazwy skrótu na **Start** menu.  
  
- Następujące właściwości są ustawiane w **wymagania wstępne** okno dialogowe, dostępne z **Publikuj** strony.  
  
- `BootstrapperEnabled` Określa, czy mają zostać wygenerowane *setup.exe* programu inicjującego.  
  
- `IsWebBootstrapper` Określa, czy *setup.exe* program inicjujący działa w trybie opartej na dyskach lub w sieci Web.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL "," SupportUrl "," PublishURL "i" UpdateURL  
 W poniższej tabeli przedstawiono cztery opcje adres URL dla wdrażania ClickOnce.  
  
|Opcja adresu URL|Opis|  
|----------------|-----------------|  
|`PublishURL`|Wymagane, jeśli w przypadku publikowania aplikacji ClickOnce do witryny sieci Web.|  
|`InstallURL`|Opcjonalna. Ustaw tę opcję, adres URL, jeśli witryna instalacji różni się od `PublishURL`. Na przykład można ustawić `PublishURL` ścieżka FTP i zestaw `InstallURL` do adresu URL sieci Web.|  
|`SupportURL`|Opcjonalna. Ustaw tę opcję, adres URL, jeśli witrynie pomocy technicznej jest inny niż `PublishURL`. Na przykład można ustawić `SupportURL` do witryny sieci Web pomocy technicznej klienta w firmie.|  
|`UpdateURL`|Opcjonalna. Ustaw tę opcję, adres URL, jeśli lokalizacji aktualizacji różni się od `InstallURL`. Na przykład można ustawić `PublishURL` ścieżka FTP i zestaw `UpdateURL` do adresu URL sieci Web.|  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)