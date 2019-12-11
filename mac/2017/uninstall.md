---
title: Odinstaluj Visual Studio dla komputerów Mac
description: Instrukcje dotyczące odinstalowywania Visual Studio dla komputerów Mac i narzędzi pokrewnych.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 78bf7fce98f2a77e05a3fbbd31afcf3f20d97a9f
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985140"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Odinstalowywanie Visual Studio dla komputerów Mac

Istnieje kilka produktów platformy Xamarin, które umożliwiają Programowanie aplikacji dla wielu platform, w tym aplikacje autonomiczne, takie jak Visual Studio dla komputerów Mac.

Możesz użyć tego przewodnika, aby odinstalować każdy produkt osobno, przechodząc do odpowiedniej sekcji lub można użyć skryptów dostępnych w sekcji [Odinstalowywanie skryptu](#uninstall-script) w celu odinstalowania wszystkiego.

Jeśli wcześniej zainstalowano Xamarin Studio na maszynie, w uzupełnieniu do poniższych kroków może być również konieczne wykonanie instrukcji dotyczących [odinstalowywania programu Xamarin](/xamarin/cross-platform/get-started/installation/uninstalling-xamarin#uninstall-xamarin-studio-on-mac) .

## <a name="uninstall-script"></a>Odinstaluj skrypt

Istnieją dwa skrypty, których można użyć do odinstalowania Visual Studio dla komputerów Mac i wszystkich składników maszyny:

- [Visual Studio i Xamarin Script](#visual-studio-for-mac-and-xamarin-script)
- [Skrypt .NET Core](#net-core-script)

Poniższe sekcje zawierają informacje dotyczące pobierania i używania skryptów.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Skrypt Visual Studio dla komputerów Mac i Xamarin

Można odinstalować programy Visual Studio i Xamarin w jednym z nich za pomocą [skryptu dezinstalacji](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Ten skrypt dezinstalacji zawiera większość poleceń, które znajdziesz w artykule. Istnieją trzy główne pominięcia ze skryptu i nie są uwzględniane ze względu na możliwe zależności zewnętrzne. Aby usunąć ten problem, przejdź do odpowiedniej sekcji poniżej i usuń je ręcznie:

- **[Odinstalowywanie narzędzia mono](#uninstall-mono-sdk-mdk)**
- **[Odinstalowywanie AVD systemu Android](#uninstall-android-avd)**
- **[Odinstalowywanie Android SDK i zestawu Java SDK](#uninstall-android-sdk-and-java-sdk)**

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy skrypt i wybierz polecenie **Zapisz jako** , aby zapisać plik na komputerze Mac.
2. Otwórz Terminal i zmień katalog roboczy na lokalizację, w której został pobrany skrypt:

    ```bash
    cd /location/of/file
    ```

3. Utwórz plik wykonywalny skryptu i uruchom go z **sudo**:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Na koniec Usuń skrypt dezinstalacji.

### <a name="net-core-script"></a>Skrypt .NET Core

Skrypt dezinstalacji programu .NET Core znajduje się w [repozytorium interfejsu wiersza polecenia dotnet](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy skrypt i wybierz polecenie **Zapisz jako** , aby zapisać plik na komputerze Mac.
2. Otwórz Terminal i zmień katalog roboczy na lokalizację, w której został pobrany skrypt:

    ```bash
    cd /location/of/file
    ```

3. Utwórz plik wykonywalny skryptu i uruchom go z **sudo**:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Na koniec Usuń skrypt dezinstalacji programu .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Odinstaluj Visual Studio dla komputerów Mac

Pierwszym krokiem w odinstalowaniu programu Visual Studio z komputera Mac jest znalezienie **programu Visual Studio. app** w katalogu **/aplikacje** i przeciągnięcie go do **kosza**. Alternatywnie kliknij prawym przyciskiem myszy i wybierz pozycję **Przenieś do kosza** , jak pokazano na poniższej ilustracji:

![Przenoszenie aplikacji Visual Studio do kosza](media/uninstall-image1.png)

Usunięcie tego zbioru aplikacji spowoduje usunięcie Visual Studio dla komputerów Mac, nawet jeśli inne pliki powiązane z platformą Xamarin nadal znajdują się w systemie plików.

Aby usunąć wszystkie ślady Visual Studio dla komputerów Mac, uruchom następujące polecenia w terminalu:

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

Może być również konieczne usunięcie następującego katalogu zawierającego różne pliki i foldery platformy Xamarin. Jednak należy pamiętać, że ten katalog zawiera klucze podpisywania systemu Android. Aby uzyskać więcej informacji, zobacz sekcję **[odinstalowywanie Android SDK i zestawu Java SDK](#uninstall-android-sdk-and-java-sdk)** :

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Odinstaluj zestaw mono SDK (MDK)

Mono to implementacja typu "open source" firmy Microsoft .NET Framework i jest używana przez wszystkie produkty platformy Xamarin — Xamarin. iOS, Xamarin. Android i Xamarin. Mac, aby umożliwić programowanie tych platform w C#programie.

> [!WARNING]
> Istnieją inne aplikacje poza Visual Studio dla komputerów Mac, które również używają narzędzia mono, takiego jak Unity.
> Przed odinstalowaniem narzędzia mono upewnij się, że nie ma innych zależności.

Aby usunąć platformę mono z komputera, uruchom następujące polecenia w terminalu:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Uninstall Xamarin.Android

Istnieje wiele elementów wymaganych do instalacji i korzystania z platformy Xamarin. Android, takich jak Android SDK i zestaw Java SDK.

Użyj następujących poleceń, aby usunąć platformę Xamarin. Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Odinstalowywanie Android SDK i zestawu Java SDK

Android SDK jest wymagana do tworzenia aplikacji dla systemu Android. Aby całkowicie usunąć wszystkie części Android SDK, Znajdź plik w lokalizacji **~/Library/Developer/Xamarin/** i przenieś go do **kosza**.

> [!WARNING]
> Należy pamiętać, że klucze podpisywania systemu Android, które są generowane przez Visual Studio dla komputerów Mac, znajdują się w `~/Library/Developer/Xamarin/Keystore`. Upewnij się, że odpowiednie kopie zapasowe zostały odpowiednio wykonane, lub Unikaj usuwania tego katalogu, jeśli chcesz zachować Magazyn kluczy.

Zestawu Java SDK (JDK) nie trzeba odinstalowywać, ponieważ jest już wstępnie spakowany jako część Mac OS X/macOS.

### <a name="uninstall-android-avd"></a>Odinstaluj AVD systemu Android

> [!WARNING]
> Istnieją inne aplikacje poza Visual Studio dla komputerów Mac, które również używają systemu Android AVD i tych dodatkowych składników systemu Android, takich jak Android Studio. usunięcie tego katalogu może spowodować przerwanie projektów w Android Studio.

Aby usunąć wszystkie AVDs systemu Android i dodatkowe składniki systemu Android, użyj następującego polecenia:

```bash
rm -rf ~/.android
```

Aby usunąć tylko AVDs systemu Android, użyj następującego polecenia:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Odinstalowywanie platformy Xamarin. iOS

Platforma Xamarin. iOS umożliwia tworzenie aplikacji dla C# systemu F# iOS przy użyciu programu lub z Visual Studio dla komputerów Mac.

Użyj następujących poleceń w terminalu, aby usunąć wszystkie pliki Xamarin. iOS z systemu plików:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Uninstall Xamarin.Mac

Program Xamarin. Mac można usunąć z maszyny przy użyciu następujących dwóch poleceń w celu wyeliminowania produktu i licencji z komputera Mac odpowiednio:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Odinstaluj skoroszyty i inspektor

Począwszy od 1.2.2, Xamarin Workbooks Inspektor & można odinstalować z terminalu, uruchamiając następujące polecenie:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

W przypadku starszych wersji należy ręcznie usunąć następujące artefakty:

* Usuń aplikację skoroszyty pod adresem `"/Applications/Xamarin Workbooks.app"`
* Usuń aplikację inspektora pod adresem `"Applications/Xamarin Inspector.app"`
* Usuń dodatki: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` i `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Usuń Inspektor i pliki pomocnicze tutaj: `/Library/Frameworks/Xamarin.Interactive.framework` i `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Odinstaluj Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Odinstaluj Instalator programu Visual Studio

Użyj następujących poleceń, aby usunąć wszystkie ślady programu Xamarin Universal Installer:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Zobacz także

- [Odinstalowywanie programu Visual Studio (w systemie Windows)](/visualstudio/install/uninstall-visual-studio)