---
title: Odinstalowywanie programu Visual Studio dla komputerów Mac
description: Instrukcje dotyczące odinstalowywania programu Visual Studio dla komputerów Mac i powiązanych narzędzi.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: ad0be8546b88fbd01f54faf7eb00f71ddd6aa632
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "76892158"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Odinstalowywanie programu Visual Studio dla komputerów Mac

Istnieje wiele produktów platformy Xamarin, które umożliwiają tworzenie aplikacji między platformami, w tym autonomiczne aplikacje, takie jak Visual Studio dla komputerów Mac.

Za pomocą tego przewodnika można odinstalować każdy produkt indywidualnie, przechodząc do odpowiedniej sekcji lub użyć skryptów podanych w sekcji [Odinstaluj skrypt,](#uninstall-script) aby odinstalować wszystko.

## <a name="uninstall-script"></a>Odinstaluj skrypt

Istnieją dwa skrypty, które mogą służyć do odinstalowywania programu Visual Studio dla komputerów Mac i wszystkie składniki dla komputera:

- [Visual Studio i skrypt platformy Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Skrypt core platformy .NET](#net-core-script)

Poniższe sekcje zawierają informacje na temat pobierania i używania skryptów.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Visual Studio dla komputerów Mac i skrypt platformy Xamarin

Składniki programu Visual Studio i Xamarin można odinstalować za jednym zamachem za pomocą [skryptu odinstalowywania](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Ten skrypt odinstalowywania zawiera większość poleceń, które znajdziesz w artykule. Istnieją trzy główne pominięcia ze skryptu i nie są uwzględniane ze względu na możliwe zależności zewnętrzne. Aby to usunąć, przejdź do odpowiedniej sekcji poniżej i usuń je ręcznie:

- **[Odinstalowywanie mono](#uninstall-mono-sdk-mdk)**
- **[Odinstalowywanie androida AVD](#uninstall-android-avd)**
- **[Odinstalowywanie pakietów SDK systemu Android i java SDK](#uninstall-android-sdk-and-java-sdk)**

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy skrypt i wybierz pozycję **Zapisz jako,** aby zapisać plik na komputerze Mac.
2. Otwórz terminal i zmień katalog roboczy na miejsce, w którym został pobrany skrypt:

    ```bash
    cd /location/of/file
    ```

3. Spraw, aby skrypt był wykonywalny i uruchom go z **sudo:**

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Na koniec usuń skrypt odinstalowywania.

### <a name="net-core-script"></a>Skrypt core platformy .NET

Skrypt odinstalowywania dla .NET Core znajduje się w [repo dotnet cli](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Aby uruchomić skrypt, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy skrypt i wybierz pozycję **Zapisz jako,** aby zapisać plik na komputerze Mac.
2. Otwórz terminal i zmień katalog roboczy na miejsce, w którym został pobrany skrypt:

    ```bash
    cd /location/of/file
    ```

3. Spraw, aby skrypt był wykonywalny i uruchom go z **sudo:**

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Na koniec usuń skrypt odinstalowywania rdzenia .NET.

## <a name="uninstall-visual-studio-for-mac"></a>Odinstalowywanie programu Visual Studio dla komputerów Mac

Pierwszym krokiem odinstalowywania programu Visual Studio z komputera Mac jest zlokalizowanie **aplikacji Visual Studio.app** w katalogu **/Applications** i przeciągnij je do **kosza.** Możesz też kliknąć prawym przyciskiem myszy i wybrać pozycję **Przenieś do Kosza,** jak pokazano na poniższej ilustracji:

![Przenoszenie aplikacji programu Visual Studio do kosza](media/uninstall-image1.png)

Usunięcie tego pakietu aplikacji powoduje usunięcie programu Visual Studio dla komputerów Mac, nawet jeśli w systemie plików mogą znajdować się inne pliki związane z platformą Xamarin.

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

Można również usunąć następujący katalog zawierający różne pliki i foldery platformy Xamarin. Jednak zanim to zrobisz, należy pamiętać, że ten katalog zawiera klucze podpisywania systemu Android. Aby uzyskać więcej informacji, zobacz sekcję **[Odinstalowywanie sdk android i java SDK](#uninstall-android-sdk-and-java-sdk)**:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Odinstaluj mono SDK (MDK)

Mono jest implementacją open source programu Microsoft .NET Framework i jest używany przez wszystkie produkty platformy Xamarin — Xamarin.iOS, Xamarin.Android i Xamarin.Mac, aby umożliwić rozwój tych platform w języku C#.

> [!WARNING]
> Istnieją inne aplikacje poza Visual Studio dla komputerów Mac, które również używają mono, takich jak Unity.
> Upewnij się, że nie ma żadnych innych zależności od mono przed odinstalowaniem go.

Aby usunąć mono framework z komputera, uruchom następujące polecenia w terminalu:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Odinstaluj xamarin.Android

Istnieje wiele elementów wymaganych do instalacji i używania platformy Xamarin.Android, takich jak zestaw SDK systemu Android i zestaw Java SDK.

Użyj następujących poleceń, aby usunąć xamarin.Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Odinstalowywanie sdk Android i java SDK

SDK systemu Android jest wymagany do tworzenia aplikacji dla systemu Android. Aby całkowicie usunąć wszystkie części zestawu SDK systemu Android, zlokalizuj plik w **~/Library/Developer/Xamarin/** i przenieś go do **Kosza**.

> [!WARNING]
> Należy pamiętać, że klucze podpisywania systemu Android generowane `~/Library/Developer/Xamarin/Keystore`przez program Visual Studio dla komputerów Mac znajdują się w programie . Jeśli chcesz zachować magazyn kluczy, należy wykonać ich utworzenie kopii zapasowej lub uniknąć usunięcia tego katalogu.

Java SDK (JDK) nie musi być odinstalowany, ponieważ jest już wstępnie spakowany jako część Systemu Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Odinstaluj Android AVD

> [!WARNING]
> Istnieją inne aplikacje poza Visual Studio dla komputerów Mac, które również używają android AVD i te dodatkowe składniki systemu Android, takich jak Android Studio.Usuwanie tego katalogu może spowodować projekty do przerwania w Programie Android Studio.

Aby usunąć wszystkie avds Systemu Android i dodatkowe składniki systemu Android należy użyć następującego polecenia:

```bash
rm -rf ~/.android
```

Aby usunąć tylko avds Systemu Android należy użyć następującego polecenia:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Odinstaluj plik Xamarin.iOS

Xamarin.iOS umożliwia tworzenie aplikacji systemu iOS przy użyciu języka C# lub F# z programem Visual Studio dla komputerów Mac.

Użyj następujących poleceń w terminalu, aby usunąć wszystkie pliki Xamarin.iOS z systemu plików:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Odinstaluj xamarin.Mac

Xamarin.Mac można usunąć z komputera za pomocą następujących dwóch poleceń, aby wyeliminować produkt i licencję z komputera Mac odpowiednio:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Odinstalowywanie skoroszytów i inspektora

Począwszy od 1.2.2, skoroszyty platformy Xamarin & Inspector można odinstalować z terminala, uruchamiając:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

W przypadku starszych wersji należy ręcznie usunąć następujące artefakty:

* Usuwanie aplikacji Skoroszyty w`"/Applications/Xamarin Workbooks.app"`
* Usuń aplikację Inspektor przy`"Applications/Xamarin Inspector.app"`
* Usuń dodatki: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` i`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Usuń inspektora i pliki `/Library/Frameworks/Xamarin.Interactive.framework` pomocnicze tutaj: i`/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Odinstalowywanie programu Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Odinstalowywanie Instalatora programu Visual Studio

Użyj następujących poleceń, aby usunąć wszystkie ślady Instalatora uniwersalnego platformy Xamarin:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Zobacz też

- [Odinstalowywanie programu Visual Studio (w systemie Windows)](/visualstudio/install/uninstall-visual-studio)