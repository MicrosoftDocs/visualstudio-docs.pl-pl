---
title: Projektant manifestu VSIX | Microsoft Docs
description: Dowiedz się, jak projektant manifestu VSIX modyfikuje plik manifestu pakietu VSIX, który ustawia zachowanie instalacji rozszerzenia programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6323b4330279848bc0453bdc7413904e2582d13a
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863964"
---
# <a name="vsix-manifest-designer"></a>Projektant manifestu VSIX
Modyfikuje plik manifestu pakietu VSIX, który ustawia zachowanie instalacji rozszerzenia programu Visual Studio.

 **Projektant manifestu VSIX** mapuje na bazowy schemat VSIX. Każdy element w schemacie można ustawić przy użyciu odpowiadającego im formantu w projektancie. Aby uzyskać więcej informacji na temat schematu, zobacz [odwołanie do schematu rozszerzenia VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Aby otworzyć **projektanta manifestu VSIX**, zlokalizuj plik *source. Extension. vsixmanifest* w **Eksplorator rozwiązań** i Otwórz plik. Jeśli plik nie zawiera prawidłowego kodu XML, projektant manifestu nie zostanie otwarty.

> [!NOTE]
> Plik *source. Extension. vsixmanifest* jest wyprowadzany do *rozszerzenia vsixmanifest* , gdy pakiet został skompilowany.

## <a name="uielement-list"></a>Lista elementów UIElement
 **Projektant manifestu VSIX** zawiera cztery sekcje, które odpowiadają tym elementom najwyższego poziomu schematu:

- Metadane

- Zainstaluj elementy docelowe

- Elementy zawartości

- Zależności

  Obszar nagłówka zawiera następujące kontrolki.

  **Nazwa produktu** Opisuje nazwę rozszerzenia.

  **Identyfikator produktu** Określa unikatowe informacje identyfikacyjne dla tego pakietu.

  **Autor** Określa nazwę autora rozszerzenia.

  **Wersja** Określa numer wersji rozszerzenia.

  Karta **metadane** zawiera następujące kontrolki.

  **Opis** Zawiera opis tekstowy rozszerzenia, który będzie wyświetlany w **Menedżerze rozszerzeń**.

  **Język** Określa domyślny język pakietu, który odnosi się do danych tekstowych w manifeście. Ten `Language` atrybut jest zgodny z Konwencją kodu ustawień regionalnych środowiska uruchomieniowego języka wspólnego (CLR) dla zestawów zasobów, na przykład en-us, EN, fr-fr. Domyślnie wartość jest neutralna, co oznacza, że pakiet zostanie uruchomiony w dowolnej wersji językowej programu Visual Studio.

  **Licencja** Określa plik tekstowy, który zawiera licencję użytkownika, jeśli jest obecny.

  **Ikona** Określa plik grafiki (*PNG*, *BMP*, *JPEG*, *ICO*), który zawiera ikonę, która będzie wyświetlana w **Menedżerze rozszerzeń**, jeśli jest obecna ikona. Obraz ikony musi być 32x32 pikseli lub jest zmieniany na te wymiary. Jeśli ikona nie zostanie określona, **Menedżer rozszerzeń** używa domyślnej ikony.

  **Podgląd obrazu** Określa plik grafiki (*PNG*, *BMP*, *JPEG*, *ICO*), który zawiera obraz podglądu, który będzie wyświetlany w **Menedżerze rozszerzeń**, jeśli obraz podglądu jest obecny. Obraz podglądu musi być 200x200 pikseli. Jeśli obraz podglądu nie zostanie określony, **Menedżer rozszerzeń** używa obrazu domyślnego.

  **Tagi** Dodaje Tagi tekstowe, które będą używane na potrzeby wskazówek wyszukiwania.

  **Informacje o wersji** Określa plik (*. txt*, *. rtf*), który zawiera informacje o wersji. Pobiera również adres URL witryny sieci Web, która wyświetla informacje o wersji.

  **Przewodnik wprowadzenie** Określa plik (*. txt*, *. rtf*), który zawiera informacje o sposobach używania rozszerzenia lub zawartości w pakiecie VSIX. Ten przewodnik pojawia się po zakończeniu instalacji rozszerzenia. Pobiera również adres URL witryny sieci Web, która wyświetla przewodnik.

  **Adres URL dodatkowych informacji** Określa adres URL witryny sieci Web zawierającej dodatkowe informacje o produkcie.

  Karta **elementy docelowe instalacji** zawiera następujące kontrolki.

  **Typ instalacji** Wyświetla listę **rozszerzeń rozszerzenia programu Visual Studio** i **zestaw SDK rozszerzeń** jako docelowe typy instalacji. Opcje różnią się w zależności od wybranego typu.

  **Rozszerzenie programu Visual Studio** Wyświetla listę elementów **InstallationTarget** , które opisują, w jaki sposób można zainstalować pakiet oraz do którego produktów Visual Studio można zainstalować to rozszerzenie. Każdy produkt jest identyfikowany oddzielnie według nazwy i wersji lub zakresu wersji. Produkty można dodawać do listy, modyfikować i usuwać. Nazwa i wersja produktu odpowiadają atrybutom **ID** i **Version** skojarzonego elementu **InstallationTarget** .

  **Zakresem wersji** jest [12,0, 14,0] i używa następującej notacji:

- [-minimalna wersja włącznie

- ] — Maksymalna wersja włącznie

- (-minimalna wersja na wyłączność

- ) — Maksymalna wersja na wyłączność

- Jedna wersja # — tylko określona wersja

  **Zestaw SDK rozszerzeń** Określa instalację globalną, która nie należy do zakresu określonego produktu i wersji. **Identyfikator platformy docelowej** to platforma, na przykład "system Windows", dla którego jesteś ukierunkowana. **Wersja platformy docelowej** to wersja, na przykład 8,0, platformy docelowej. **Nazwa zestawu** SDK i **wersja zestawu** SDK są odpowiednio nazwami i numerami wersji zestawu SDK.

  **Ten VSIX jest instalowany dla wszystkich użytkowników (wymaga podniesienia uprawnień przy instalacji)** Jeśli zaznaczysz to pole wyboru, rozszerzenie zostanie zainstalowane dla wszystkich użytkowników. w przeciwnym razie jest zainstalowana tylko dla bieżącego użytkownika.

  **Ten VSIX jest instalowany przez Instalator Windows** Jeśli zaznaczysz to pole wyboru, rozszerzenie zostanie zainstalowane przez Instalator Windows (plik *MSI* ); w przeciwnym razie jest instalowany jako typowy pakiet VSIX (plik *VSIX* ).

  Karta **zasoby** zawiera następujące kontrolki.

  **Lista zasobów** Wyświetla listę elementów zawartości, które opisują elementy rozszerzenia lub treści, które są używane przez ten pakiet. Każde rozszerzenie lub element zawartości jest wymieniany oddzielnie według źródła, typu i ścieżki. Rozszerzenia i elementy zawartości można dodawać do listy, modyfikować i usuwać. Typ i ścieżka elementu Extension lub Content odpowiada `Type` `Path` atrybutom i skojarzonego `Asset` elementu. Znane są następujące typy:

- Microsoft. VisualStudio. Package

- Microsoft. VisualStudio. MefComponent

- Microsoft. VisualStudio. ToolboxControl

- Microsoft. VisualStudio. Samples

- Microsoft. VisualStudio. ProjectTemplate

- Microsoft. VisualStudio. ItemTemplate

- Microsoft. VisualStudio. Assembly

- Microsoft. ExtensionSDK

  Aby dodać lub edytować element zawartości, należy określić typ zasobu, czy element zawartości jest projektem w bieżącym rozwiązaniu lub pliku w systemie plików oraz nazwą projektu. Możesz również określić nazwę folderu, który ma zostać osadzony.

  Możesz również utworzyć własne typy i nadać im unikatowe nazwy.

  Karta **zależności** zawiera następujące kontrolki.

  **Nazwa, źródło i zakres wersji** Wyświetla listę elementów zależności tego pakietu, które są zależne od innych pakietów, od których zależy ten pakiet. Jeśli zostanie określony pakiet zależności, należy go zainstalować przed zainstalowaniem tego pakietu. w przeciwnym razie ten pakiet musi zostać zainstalowany.

  Pakiety zależności są określane przez identyfikator, nazwę, zakres wersji, źródło i sposób, w jaki ma zostać rozwiązany zależność. Każdy pakiet zależności jest wyświetlany osobno według nazwy, wersji i źródła. Pakiety zależności można dodawać do listy, modyfikować i usuwać.

  Identyfikator musi być zgodny z `ID` atrybutem metadanych pakietu zależności. Źródłem może być projekt w bieżącym rozwiązaniu, aktualnie zainstalowanym rozszerzeniu lub pliku. Ustawienie **How to rerozwiązało zależność** może być ścieżką względną do zagnieżdżonego pakietu lub adresem URL lokalizacji pobierania dla zależności. Identyfikator, wersja i rozdzielczość pakietu zależności odpowiadają `Id` , `Version` i `Location` atrybuty `Dependency` elementu skojarzonego.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja schematu rozszerzenia VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
