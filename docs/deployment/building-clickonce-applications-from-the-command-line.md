---
title: Tworzenie aplikacji ClickOnce z wiersza polecenia | Microsoft Docs
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
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797203"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Tworzenie aplikacji ClickOnce z wiersza poleceń
W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]można kompilować projekty z wiersza polecenia, nawet jeśli są tworzone w zintegrowanym środowisku programistycznym (IDE). W rzeczywistości można skompilować projekt utworzony przy użyciu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] na innym komputerze, na którym zainstalowano tylko .NET Framework. Pozwala to na odtworzenie kompilacji przy użyciu zautomatyzowanego procesu, na przykład w centralnym laboratorium kompilacji lub użycie zaawansowanych technik tworzenia skryptów poza zakresem tworzenia projektu.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Używanie programu MSBuild do odtwarzania wdrożeń aplikacji ClickOnce
 Po wywołaniu MSBuild/target: Opublikuj w wierszu polecenia, nakazuje systemowi MSBuild skompilowanie projektu i utworzenie aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] w folderze publikacji. Jest to równoznaczne z wybraniem polecenia **Publikuj** w IDE.

 To polecenie uruchamia program *MSBuild. exe*, który znajduje się na ścieżce w środowisku wiersza polecenia programu Visual Studio.

 "Target" to wskaźnik do programu MSBuild dotyczący sposobu przetwarzania polecenia. Kluczowe cele to element docelowy "build" i element docelowy "publish". Obiekt docelowy kompilacji jest równoznaczny z wybraniem polecenia Build (lub naciśnięciem klawisza F5) w środowisku IDE. Jeśli chcesz tylko skompilować projekt, możesz to osiągnąć, wpisując `msbuild`. To polecenie działa, ponieważ obiekt docelowy kompilacji jest domyślnym obiektem docelowym dla wszystkich projektów generowanych przez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Oznacza to, że nie trzeba jawnie określać docelowej kompilacji. W związku z tym wpisywanie `msbuild` jest tą samą operacją co `msbuild /target:build`.

 Polecenie `/target:publish` instruuje MSBuild, aby wywołał element docelowy publikowania. Element docelowy publikowania zależy od docelowej kompilacji. Oznacza to, że operacja publikowania jest nadzbiorem operacji kompilacji. Na przykład jeśli została wprowadzona zmiana do jednego z Visual Basic lub C# plików źródłowych, odpowiedni zestaw zostanie automatycznie odbudowany przez operację publikowania.

 Aby uzyskać informacje na temat generowania pełnego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu narzędzia wiersza polecenia programu Mage. exe do tworzenia manifestu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Tworzenie i kompilowanie podstawowej aplikacji ClickOnce przy użyciu programu MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Aby utworzyć i opublikować projekt ClickOnce

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    Wybierz szablon projektu **aplikacji pulpitu systemu Windows** i nadaj nazwę projektowi `CmdLineDemo`.

1. W menu **kompilacja** kliknij polecenie **Publikuj** .

    Ten krok zapewnia, że projekt jest prawidłowo skonfigurowany do tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji.

    Pojawi się kreator publikacji.

1. W Kreatorze publikacji kliknij przycisk **Zakończ**.

    Program Visual Studio generuje i wyświetla domyślną stronę sieci Web o nazwie *Publish. htm*.

1. Zapisz projekt i zanotuj lokalizację folderu, w którym jest przechowywana.

   W powyższych krokach utworzysz projekt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], który został opublikowany po raz pierwszy. Teraz można odtworzyć kompilację poza IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Aby odtworzyć kompilację z wiersza polecenia

1. Zakończ [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. W menu **Start** systemu Windows kliknij pozycję **Wszystkie programy**, a następnie **Microsoft Visual Studio**, a następnie **Visual Studio Tools**, **wiersz polecenia programu Visual Studio**. W tym celu należy otworzyć wiersz polecenia w folderze głównym bieżącego użytkownika.

3. W **wierszu polecenia programu Visual Studio**Zmień bieżący katalog na lokalizację projektu, który właśnie został skompilowany. Na przykład wpisz `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Aby usunąć istniejące pliki utworzone w ramach "aby utworzyć i opublikować projekt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]," wpisz `rmdir /s publish`.

    Ten krok jest opcjonalny, ale zapewnia, że nowe pliki zostały utworzone przez kompilację w wierszu polecenia.

5. Typ `msbuild /target:publish`.

   Powyższe kroki spowodują utworzenie pełnego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji w podfolderze projektu o nazwie **Publikuj**. *CmdLineDemo. Application* to manifest wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Folder *CmdLineDemo_1.0.0.0* zawiera pliki *CmdLineDemo. exe* i *CmdLineDemo. exe. manifest*, manifest aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. *Setup. exe* to program inicjujący, który jest domyślnie skonfigurowany do instalowania .NET Framework. Folder DotNetFX zawiera pakiety redystrybucyjne dla .NET Framework. Jest to cały zestaw plików potrzebnych do wdrożenia aplikacji za pośrednictwem sieci Web lub UNC lub CD/DVD.
   
> [!NOTE]
> System MSBuild używa opcji **PublishDir** , aby określić lokalizację danych wyjściowych, na przykład `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Właściwości publikowania
 Po opublikowaniu aplikacji w powyższych procedurach Kreator publikacji dodaje następujące właściwości do pliku projektu. Te właściwości bezpośrednio wpływają na sposób tworzenia aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

 W *CmdLineDemo. vbproj* / *CmdLineDemo. csproj*:

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

 Każdą z tych właściwości można przesłonić w wierszu polecenia bez zmiany samego pliku projektu. Na przykład następujące polecenie spowoduje skompilowanie wdrożenia aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bez programu inicjującego:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Właściwości publikowania są kontrolowane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na stronach właściwości **Publikowanie**, **zabezpieczenia**i **podpisywanie** w **projektancie projektu**. Poniżej znajduje się opis właściwości publikowania wraz ze wskazaniem, jak każdy z nich jest ustawiany na różnych stronach właściwości projektanta aplikacji:

- `AssemblyOriginatorKeyFile` określa plik klucza używany do podpisywania manifestów aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Ten sam klucz może być również używany do przypisywania silnej nazwy do zestawów. Ta właściwość jest ustawiana na stronie **podpisywanie** w **projektancie projektu**.

  Na stronie **zabezpieczenia** są ustawione następujące właściwości:

- **Włącz ustawienia zabezpieczeń ClickOnce** określają, czy są generowane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów. Podczas pierwszego tworzenia projektu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generowanie manifestu jest domyślnie wyłączone. Kreator automatycznie włączy tę flagę przy publikowaniu po raz pierwszy.

- **TargetZone** określa poziom zaufania, który ma być emitowany do manifestu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Możliwe wartości to "Internet", "LocalIntranet" i "Custom". Internet i LocalIntranet spowodują, że domyślny zestaw uprawnień zostanie wyemitowany do manifestu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. LocalIntranet jest wartością domyślną i zasadniczo oznacza pełne zaufanie. Niestandardowy określa, że tylko uprawnienia określone w *aplikacji podstawowej. plik manifestu* ma być emitowany do manifestu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Plik *App. manifest* to częściowy plik manifestu, który zawiera tylko definicje informacji o zaufaniu. Jest to ukryty plik, automatycznie dodawany do projektu podczas konfigurowania uprawnień na stronie **zabezpieczenia** .

  Na stronie **Publikowanie** są ustawiane następujące właściwości:

- `PublishUrl` to lokalizacja, w której aplikacja zostanie opublikowana w środowisku IDE. Jest wstawiany do manifestu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], jeśli nie określono właściwości `InstallUrl` lub `UpdateUrl`.

- `ApplicationVersion` określa wersję aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Jest to czterocyfrowy numer wersji. Jeśli Ostatnia cyfra to "*", `ApplicationRevision` jest zastępowana dla wartości wstawionej do manifestu w czasie kompilacji.

- `ApplicationRevision` określa poprawkę. Jest to liczba całkowita, która zwiększa się przy każdym publikowaniu w środowisku IDE. Należy zauważyć, że nie jest on automatycznie zwiększany dla kompilacji wykonywanych w wierszu polecenia.

- `Install` określa, czy aplikacja jest zainstalowaną aplikacją czy aplikacją uruchomieniową z sieci Web.

- `InstallUrl` (niepokazywany) to lokalizacja, w której użytkownicy będą instalować aplikację. Jeśli jest określony, ta wartość jest nagrywana do programu inicjującego *Setup. exe* , jeśli właściwość `IsWebBootstrapper` jest włączona. Jest również wstawiany do manifestu aplikacji, jeśli nie określono `UpdateUrl`.

- `SupportUrl` (niepokazywany) to lokalizacja połączona w oknie dialogowym **Dodawanie/usuwanie programów** dla zainstalowanej aplikacji.

  W oknie dialogowym **aktualizacje aplikacji** są ustawiane następujące właściwości, do których można uzyskać dostęp ze strony **Publikowanie** .

- `UpdateEnabled` wskazuje, czy aplikacja ma sprawdzać dostępność aktualizacji.

- `UpdateMode` określa aktualizacje na pierwszym planie lub aktualizacje w tle.

- `UpdateInterval` określa, jak często aplikacja ma sprawdzać dostępność aktualizacji.

- `UpdateIntervalUnits` określa, czy wartość `UpdateInterval` jest wyrażona w jednostkach godzin, dni czy tygodni.

- `UpdateUrl` (niepokazywany) jest lokalizacją, z której aplikacja będzie otrzymywać aktualizacje. Jeśli jest określony, ta wartość jest wstawiana do manifestu aplikacji.

  Następujące właściwości są ustawiane w oknie dialogowym **Opcje publikowania** dostępnym ze strony **publikowania** .

- `PublisherName` określa nazwę wydawcy wyświetlanego w monicie wyświetlanym podczas instalowania lub uruchamiania aplikacji. W przypadku zainstalowanej aplikacji jest również używana do określania nazwy folderu w menu **Start** .

- `ProductName` określa nazwę produktu wyświetlanego w monicie wyświetlanym podczas instalowania lub uruchamiania aplikacji. W przypadku zainstalowanej aplikacji jest również używana do określania nazwy skrótu w menu **Start** .

  Następujące właściwości są ustawiane w oknie dialogowym **wymagania wstępne** , do którego dostęp można uzyskać ze strony **Publikowanie** .

- `BootstrapperEnabled` określa, czy generować program inicjujący *Setup. exe* .

- `IsWebBootstrapper` określa, czy program inicjujący *Setup. exe* działa za pośrednictwem sieci Web, czy w trybie opartym na dyskach.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL i UpdateURL
 W poniższej tabeli przedstawiono cztery opcje adresów URL dla wdrażania ClickOnce.

|Opcja adresu URL|Opis|
|----------------|-----------------|
|`PublishURL`|Wymagane w przypadku publikowania aplikacji ClickOnce w witrynie sieci Web.|
|`InstallURL`|Opcjonalny. Ustaw tę opcję adresu URL, Jeśli lokacja instalacji różni się od `PublishURL`. Na przykład można ustawić `PublishURL` na ścieżkę FTP i ustawić `InstallURL` na adres URL sieci Web.|
|`SupportURL`|Opcjonalny. Ustaw tę opcję adresu URL, Jeśli lokacja pomocy technicznej jest inna niż `PublishURL`. Na przykład można ustawić `SupportURL` na witrynę sieci Web pomocy technicznej dla klientów firmy.|
|`UpdateURL`|Opcjonalny. Ustaw tę opcję adresu URL, jeśli lokalizacja aktualizacji jest inna niż `InstallURL`. Na przykład można ustawić `PublishURL` na ścieżkę FTP i ustawić `UpdateURL` na adres URL sieci Web.|

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
