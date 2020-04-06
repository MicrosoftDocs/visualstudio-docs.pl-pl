---
title: Projektant manifestu VSIX | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697896"
---
# <a name="vsix-manifest-designer"></a>Projektant manifestu VSIX
Modyfikuje plik manifestu pakietu VSIX, który ustawia zachowanie instalacji dla rozszerzenia programu Visual Studio.

 Projektant **manifestu VSIX** jest mapowana do podstawowego schematu VSIX. Każdy element w schemacie można ustawić przy użyciu odpowiedniego formantu w projektancie. Aby uzyskać więcej informacji na temat schematu, zobacz [ODWOŁANIE do schematu rozszerzenia VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Aby otworzyć **projektanta manifestu VSIX,** znajdź plik *source.extension.vsixmanifest* w **Eksploratorze rozwiązań**i otwórz plik. Jeśli plik nie zawiera prawidłowego kodu XML, projektant manifestu nie zostanie otwarty.

> [!NOTE]
> Plik *source.extension.vsixmanifest* jest dostarczany do *extension.vsixmanifest,* gdy pakiet jest zbudowany.

## <a name="uielement-list"></a>Lista UIElement
 **Projektant manifestu VSIX** zawiera cztery sekcje, które odpowiadają tym elementom najwyższego poziomu schematu:

- Metadane

- Instalowanie obiektów docelowych

- Elementy zawartości

- Zależności

  Obszar nagłówka zawiera następujące formanty.

  **Nazwa produktu** Opisuje nazwę rozszerzenia.

  **Identyfikator produktu** Określa unikatowe informacje identyfikacyjne dla tego pakietu.

  **Autor** Określa nazwę autora rozszerzenia.

  **Wersja** Określa numer wersji rozszerzenia.

  Karta **Metadane** zawiera następujące kontrolki.

  **Opis** Zawiera opis tekstowy rozszerzenia, który ma być wyświetlany w **Menedżerze rozszerzeń**.

  **Język** Określa domyślny język pakietu, który odpowiada danym tekstowym w manifeście. Atrybut `Language` jest zgodny z konwencją kodu ustawień regionalnych wspólnego środowiska wykonawczego języka (CLR) dla zestawów zasobów, na przykład en-us, en, fr-fr. Domyślnie wartość jest neutralna, co oznacza, że pakiet będzie uruchamiany w dowolnej wersji językowej programu Visual Studio.

  **Licencja** Określa plik tekstowy zawierający licencję użytkownika, jeśli jest obecny.

  **Ikona** Określa plik graficzny (*.png*, *.bmp*, *.jpeg*, *.ico*), który zawiera ikonę wyświetlaną w **Menedżerze rozszerzeń**, jeśli ikona jest obecna. Obraz ikony musi mieć wymiary 32x32 pikseli lub jest zmieniany na te wymiary. Jeśli żadna ikona nie zostanie określona, **Menedżer rozszerzeń** używa domyślnej ikony.

  **Podgląd obrazu** Określa plik graficzny (*png*, *.bmp*, *.jpeg*, *.ico*), który zawiera obraz podglądu, który ma być wyświetlany w **Menedżerze rozszerzeń,** jeśli jest obecny obraz podglądu. Obraz podglądu musi mieć rozmiar 200 x 200 pikseli. Jeśli nie określono obrazu podglądu, **Menedżer rozszerzeń** używa obrazu domyślnego.

  **Tagi** Dodaje znaczniki tekstowe, które mają być używane do wskazówek dotyczących wyszukiwania.

  **Informacje o wersji** Określa plik (*.txt*, *.rtf*), który zawiera informacje o wersji. Przyjmuje również adres URL witryny sieci Web, która wyświetla informacje o wersji.

  **Przewodnik po wprowadzenie** Określa plik (*.txt*, *.rtf*), który zawiera informacje o tym, jak korzystać z rozszerzenia lub zawartości w pakiecie VSIX. Ten przewodnik pojawia się po zakończeniu instalacji rozszerzenia. Przyjmuje również adres URL witryny sieci Web, która wyświetla przewodnik.

  **Więcej informacji URL** Określa adres URL witryny sieci Web zawierającej dodatkowe informacje o produkcie.

  Karta **Zainstaluj obiekty docelowe** zawiera następujące kontrolki.

  **Typ instalacji** Wyświetla listę **rozszerzenia programu Visual Studio** i **zestawów SDK rozszerzeń** jako docelowe typy instalacji. Opcje różnią się w zależności od wybranego typu.

  **Rozszerzenie programu Visual Studio** Wyświetla listę **InstallationTarget** elementów, które opisują, jak pakiet można zainstalować i w których program visual studio produktów to rozszerzenie może być zainstalowany. Każdy produkt jest identyfikowany oddzielnie przez nazwę i zakres wersji lub wersji. Produkty można dodawać do listy, modyfikować i usuwać. Nazwa i wersja produktu odpowiadają atrybutom **Id** i **Version** skojarzonego elementu **InstallationTarget.**

  **Zakres wersji** to [12.0, 14.0] i używa następującego notacji:

- [ - minimalna wersja włącznie

- ] - maksymalna wersja włącznie

- ( - wersja minimalna wyłączna

- ) - maksymalna wersja ekskluzywna

- Pojedyncza wersja # - tylko określona wersja

  **Rozszerzenie SDK** Określa instalację globalną, która nie jest określona do określonego produktu i wersji. **Identyfikator platformy docelowej** to platforma, na przykład "Windows", na którą kierujesz reklamy. **Wersja platformy docelowej** jest wersją, taką jak 8.0, platformy docelowej. **Nazwa zestawu SDK** i **wersja zestawu SDK** to odpowiednio nazwa i numer wersji zestawu SDK.

  **Ten VSIX jest zainstalowany dla wszystkich użytkowników (wymaga podniesienia na instalację)** Jeśli zaznaczysz to pole wyboru, rozszerzenie zostanie zainstalowane dla wszystkich użytkowników; w przeciwnym razie jest zainstalowany tylko dla bieżącego użytkownika.

  **Ten vsix jest instalowany przez Instalatora Windows** Jeśli to pole wyboru zostanie zaznaczone, rozszerzenie zostanie zainstalowane przez Instalatora Windows ( plik*msi);* w przeciwnym razie jest zainstalowany jako typowy pakiet VSIX (*.vsix* file).

  Karta **Zasoby** zawiera następujące formanty.

  **Wykaz aktywów** Wyświetla listę asset elementów, które opisują rozszerzenie lub elementy zawartości, które ten pakiet powierzchni. Każdy element rozszerzenia lub zawartości jest wyświetlany oddzielnie według źródła, typu i ścieżki. Rozszerzenia i elementy zawartości można dodawać do listy, modyfikować i usuwać. Typ i ścieżka elementu rozszerzenia lub zawartości `Type` odpowiada `Path` i atrybuty `Asset` skojarzonego elementu. Znane są następujące typy:

- Pakiet Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefFirment

- Kontrola microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Płyta Microsoft.VisualStudio.ProjectTemplate

- Płyta Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Program Microsoft.ExtensionSDK

  Aby dodać lub edytować zasób, należy określić typ środka trwałego, czy zasób jest projektem w bieżącym rozwiązaniu, czy plikiem w systemie plików, a także nazwę projektu. Można również określić nazwę folderu, w którym ma być osadzony.

  Można również tworzyć własne typy i nadać im unikatowe nazwy.

  Karta **Zależności zawiera** następujące kontrolki.

  **Nazwa, źródło i zakres wersji** Wyświetla listę elementów zależności tego pakietu, które są inne pakiety, które zależy od tego pakietu. Jeśli pakiet zależności jest określony, musi być zainstalowany przed zainstalowaniem tego pakietu; w przeciwnym razie ten pakiet musi go zainstalować.

  Pakiety zależności są określone przez identyfikator, nazwę, zakres wersji, źródło i sposób rozpoznawania zależności. Każdy pakiet zależności jest wyświetlany oddzielnie według nazwy, wersji i źródła. Pakiety zależności można dodawać do listy, modyfikować i usuwać.

  Identyfikator musi być `ID` zgodny z atrybutem metadanych pakietu zależności. Źródłem może być projekt w bieżącym rozwiązaniu, aktualnie zainstalowane rozszerzenie lub plik. Ustawienie **Jak jest rozpoznawana zależność** może być względną ścieżką zagnieżdżonego pakietu lub adresem URL lokalizacji pobierania zależności. Identyfikator, wersja i rozdzielczość pakietu zależności odpowiadają `Id`, `Version`i `Location` atrybuty skojarzonego `Dependency` elementu.

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu rozszerzenia VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
