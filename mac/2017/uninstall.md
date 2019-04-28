---
title: Odinstaluj program Visual Studio dla komputerów Mac
description: Instrukcje dotyczące odinstalowywania programu Visual Studio dla komputerów Mac i pokrewnych narzędzi.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: ef9b609b74b878a2d9bdafb087481ad1c6e79a70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62986835"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Odinstalowywanie programu Visual Studio dla komputerów Mac

Istnieje wiele produktów platformy Xamarin, które umożliwiają tworzenie aplikacji dla wielu platform, w tym aplikacje autonomiczne, takimi jak Visual Studio dla komputerów Mac.

Ten przewodnik służy do odinstalowania każdego produktu oddzielnie, przechodząc do odpowiedniej sekcji lub za pomocą skryptów w [skryptu odinstalowania](#uninstall-script) sekcję dotyczącą dezinstalacji wszystko.

Jeśli użytkownik wcześniej mieli Xamarin Studio zainstalowany na komputerze może być również konieczne postępuj zgodnie z instrukcjami w [jego odinstalowanie platformy Xamarin](/xamarin/cross-platform/get-started/installation/uninstalling-xamarin#uninstall-xamarin-studio-on-mac) przewodnika następujące kroki.

## <a name="uninstall-script"></a>Odinstaluj skryptu

Istnieją dwa skrypty, które mogą służyć do odinstalowania programu Visual Studio dla komputerów Mac oraz wszystkie składniki maszyny:

- [Skrypt Visual Studio i Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Skrypt platformy .NET core](#net-core-script)

Poniższe sekcje zawierają informacje na temat pobierania i używania skryptów.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Program Visual Studio dla komputerów Mac i Xamarin skryptu

Można odinstalować programu Visual Studio i składników platformy Xamarin w jednym przejść za pomocą [odinstalować skryptu](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Ten skrypt dezinstalacji zawiera większość poleceń, które można znaleźć w artykule. Istnieją trzy główne pominięć ze skryptu i nie są włączone z powodu możliwych zależności zewnętrznych. Aby usunąć ten problem, przejdź do odpowiedniej sekcji poniżej, a następnie ręcznie usunąć:

- **[Odinstalowywanie środowiska Mono](#uninstall-mono-sdk-mdk)**
- **[Odinstalowywanie AVD systemu Android](#uninstall-android-avd)**
- **[Odinstalowanie zestawu SDK systemu Android SDK i środowiska Java](#uninstall-android-sdk-and-java-sdk)**

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy skrypt i wybierz pozycję **Zapisz jako** można zapisać pliku na komputerze Mac.
2. Otwórz Terminal i zmień katalog roboczy, do którego został pobrany skrypt:

    ```bash
    cd /location/of/file
    ```

3. Wykonywalny skrypt i uruchom ją za pomocą **"sudo"**:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Na koniec usunąć skrypt dezinstalacji.

### <a name="net-core-script"></a>Skrypt platformy .NET core

Skrypt dezinstalacji dla platformy .NET Core znajduje się w [repozytorium interfejsu wiersza polecenia platformy dotnet](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy skrypt i wybierz pozycję **Zapisz jako** można zapisać pliku na komputerze Mac.
2. Otwórz Terminal i zmień katalog roboczy, do którego został pobrany skrypt:

    ```bash
    cd /location/of/file
    ```

3. Wykonywalny skrypt i uruchom ją za pomocą **"sudo"**:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Na koniec usunąć skrypt dezinstalacji platformy .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Odinstaluj program Visual Studio dla komputerów Mac

Pierwszym krokiem podczas odinstalowywania programu Visual Studio z poziomu komputera Mac jest zlokalizowanie **Visual Studio.app** w **/Applications** katalogu i przeciągnij go do **Kosza**. Alternatywnie, kliknij prawym przyciskiem myszy i wybierz **przenieść do Kosza** jak pokazano na poniższej ilustracji:

![Przenieś Visual Studio Application do Kosza](media/uninstall-image1.png)

Usunięcie tego zbioru aplikacji spowoduje usunięcie programu Visual Studio dla komputerów Mac, mimo że może to być innych plików związanych z platformy Xamarin w dalszym ciągu w systemie plików.

Aby usunąć wszystkie ślady programu Visual Studio dla komputerów Mac, uruchom następujące polecenia w terminalu:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

Można również usunąć następującego katalogu zawierającego różnych Xamarin plików i folderów. Jednak przed wykonaniem należy pamiętać, że ten katalog zawiera Android kluczy podpisywania. Aby uzyskać więcej informacji można znaleźć w sekcji  **[odinstalowywania zestawu Android SDK i zestawu SDK Java](#uninstall-android-sdk-and-java-sdk)**:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Odinstalowywanie narzędzia Mono zestawu SDK (MDK)

Narzędzie mono jest implementacją open source firmy Microsoft .NET Framework i jest używany przez wszystkie Xamarin Products—Xamarin.iOS, Xamarin.Android i Xamarin.Mac umożliwia tworzenie tych platform w języku C#.

> [!WARNING]
> Istnieją inne aplikacje w zakresie poza programem Visual Studio dla komputerów Mac, które także używają platformy Mono, takich jak Unity.
> Pamiętaj, że żadne inne zależności na istnieją Mono przed jego odinstalowaniem.

Aby usunąć platformy Mono na komputerze, uruchom następujące polecenia w terminalu:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Uninstall Xamarin.Android

Istnieje szereg elementów wymaganych do instalacji i korzystania z platformy Xamarin.Android, takich jak zestaw SDK systemu Android i zestawu SDK języka Java.

Aby usunąć rozszerzenie Xamarin.Android, użyj następujących poleceń:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Odinstalowanie zestawu SDK systemu Android SDK i środowiska Java

Zestaw SDK systemu Android jest wymagany do tworzenia aplikacji dla systemu Android. Aby całkowicie usunąć wszystkie części zestawu Android SDK, zlokalizuj plik w rozmiarze **~/Library/Developer/Xamarin/** i przenieść ją do **Kosza**.

> [!WARNING]
> Należy pamiętać, że dla systemu Android klucze podpisywania, które są generowane przez program Visual Studio dla komputerów Mac znajdują się w `~/Library/Developer/Xamarin/Keystore`. Pamiętaj przeznaczenie tych odpowiednio lub uniknąć usuwania tego katalogu, jeśli chcesz zachować magazyn kluczy.

Zestaw SDK Java (JDK), nie trzeba dezinstalację, ponieważ już jest wstępnie dostarczana jako część systemu Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Odinstaluj AVD systemu Android

> [!WARNING]
> Istnieją inne aplikacje w zakresie poza programem Visual Studio dla komputerów Mac, które także używają urządzeń AVD systemu Android i te dodatkowe składniki systemu android, takie jak Studio.Removing dla systemu Android, w tym katalogu może spowodować, że projekty można przerwać w programie Android Studio.

Aby usunąć wszelkie AVDs dla systemu Android i Android dodatkowych składników użyj następującego polecenia:

```bash
rm -rf ~/.android
```

Aby usunąć tylko AVDs dla systemu Android, użyj następującego polecenia:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Odinstalowywanie rozszerzenia Xamarin.iOS

Xamarin.iOS umożliwia programowanie aplikacji dla systemu iOS dzięki C# lub F# z programem Visual Studio dla komputerów Mac.

Użyj następujących poleceń w terminalu, aby usunąć wszystkie pliki rozszerzenia Xamarin.iOS w systemie plików:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Uninstall Xamarin.Mac

Rozszerzenia Xamarin.Mac może zostać usunięty z Twojego komputera odpowiednio likwidacji produktu i licencji na komputerze Mac przy użyciu dwóch następujących poleceń:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Odinstaluj skoroszyty i Inspektor

Począwszy od 1.2.2 Xamarin Workbooks & Inspektor może zostać odinstalowany z poziomu terminalu, uruchamiając:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

W przypadku starszych wersji należy ręcznie usunąć następujących artefaktów:

* Usuwanie aplikacji skoroszytów w `"/Applications/Xamarin Workbooks.app"`
* Usuwanie aplikacji inspektora w `"Applications/Xamarin Inspector.app"`
* Usuń dodatki: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` i `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Usuń Inspektor i obsługi plików w tym miejscu: `/Library/Frameworks/Xamarin.Interactive.framework` i `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Odinstaluj program Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Odinstaluj Instalator programu Visual Studio

Aby usunąć wszystkie ślady Instalatora uniwersalnej platformy Xamarin, użyj następujących poleceń:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Zobacz także

- [Odinstaluj program Visual Studio (na Windows)](/visualstudio/install/uninstall-visual-studio)