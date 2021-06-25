---
title: Projektant manifestu VSIX | Microsoft Docs
description: Dowiedz się, jak projektant manifestu VSIX modyfikuje plik manifestu pakietu VSIX, który ustawia zachowanie instalacji Visual Studio rozszerzenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baea7be60c67f186da2372c4644366b4a1a7a202
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905192"
---
# <a name="vsix-manifest-designer"></a>Projektant manifestu VSIX
Modyfikuje plik manifestu pakietu VSIX, który określa zachowanie instalacji dla Visual Studio rozszerzenia.

 Projektant **manifestu VSIX mapuje** do bazowego schematu VSIX. Każdy element w schemacie można ustawić za pomocą odpowiedniej kontrolki w projektancie. Aby uzyskać więcej informacji na temat schematu, zobacz VsIX Extension Schema 2.0 Reference (Odwołanie do schematu [rozszerzenia VSIX 2.0).](../extensibility/vsix-extension-schema-2-0-reference.md)

 Aby otworzyć **projektanta manifestu VSIX,** znajdź plik *source.extension.vsixmanifest* Eksplorator rozwiązań **,** a następnie otwórz plik . Jeśli plik nie zawiera prawidłowego kodu XML, nie można otworzyć projektanta manifestu.

> [!NOTE]
> Plik *source.extension.vsixmanifest* jest wyprowadzana do *pliku extension.vsixmanifest* podczas budowie pakietu.

## <a name="uielement-list"></a>Lista UIElement
 Projektant **manifestu VSIX** zawiera cztery sekcje, które odpowiadają tym elementom najwyższego poziomu schematu:

- Metadane

- Obiekty docelowe instalacji

- Elementy zawartości

- Zależności

  Obszar nagłówka zawiera następujące kontrolki.

  **Nazwa produktu** Opisuje nazwę rozszerzenia.

  **Identyfikator produktu** Określa unikatowe informacje identyfikacyjne dla tego pakietu.

  **Autor** Określa nazwę autora rozszerzenia.

  **Wersja** Określa numer wersji rozszerzenia.

  Karta **Metadane** zawiera następujące kontrolki.

  **Opis** Zawiera opis tekstowy rozszerzenia, który ma być wyświetlany w **Menedżerze rozszerzeń**.

  **Język** Określa domyślny język pakietu, który odpowiada danych tekstowych w manifeście. Atrybut jest zgodny z konwencją kodu środowiska uruchomieniowego języka wspólnego (CLR) dla zestawów zasobów, na przykład `Language` en-us, en, fr-fr. Domyślnie wartość jest neutralna, co oznacza, że pakiet będzie uruchamiany w dowolnej wersji językowej Visual Studio.

  **Licencja** Określa plik tekstowy, który zawiera licencję użytkownika, jeśli istnieje.

  **Ikona** Określa plik graficzny *(.png*, *.bmp*, *jpeg*, *ico*) zawierający ikonę, która ma być wyświetlana w Menedżerze **rozszerzeń,** jeśli jest obecna ikona. Obraz ikony musi mieć rozmiar 32x32 piksele lub zmienić rozmiar na te wymiary. Jeśli nie określono ikony, **Menedżer rozszerzeń używa** ikony domyślnej.

  **Obraz podglądu** Określa plik graficzny *(.png*, *.bmp*, *jpeg*, *ico*) zawierający obraz podglądu, który ma być wyświetlany w Menedżerze **rozszerzeń,** jeśli jest obecny obraz podglądu. Obraz podglądu musi mieć rozmiar 200 x 200 pikseli. Jeśli nie określono obrazu podglądu, **Menedżer rozszerzeń** używa obrazu domyślnego.

  **Tagi** Dodaje tagi tekstowe, które mają być używane dla wskazówek wyszukiwania.

  **Informacje o wersji** Określa plik *(*.txt, *RTF*) zawierający informacje o wersji. Pobiera również adres URL witryny sieci Web, która wyświetla informacje o wersji.

  **Wprowadzenie przewodnik** Określa plik (*.txt*, *RTF*) zawierający informacje o sposobu korzystania z rozszerzenia lub zawartości w pakiecie VSIX. Ten przewodnik jest wyświetlany po zakończeniu instalacji rozszerzenia. Pobiera również adres URL witryny sieci Web, która wyświetla przewodnik.

  **Adres URL więcej informacji** Określa adres URL witryny sieci Web zawierającej dodatkowe informacje o produkcie.

  Karta **Obiekty docelowe** instalacji zawiera następujące kontrolki.

  **Typ instalacji** Wyświetla **Visual Studio rozszerzenia i** rozszerzenia **SDK** jako docelowe typy instalacji. Opcje różnią się w zależności od wybranego typu.

  **Visual Studio rozszerzenia** Wyświetla listę **elementów InstallationTarget,** które opisują, jak można zainstalować pakiet i w którym Visual Studio produkty, w których można zainstalować to rozszerzenie. Każdy produkt jest identyfikowany oddzielnie według nazwy i wersji lub zakresu wersji. Produkty można dodawać do listy, modyfikować i usuwać. Nazwa i wersja produktu odpowiadają atrybutom **Id** i **Version** **skojarzonego elementu InstallationTarget.**

  **Zakres wersji** to [12.0, 14.0] i używa następującej notacji:

- [ — minimalna wersja włącznie

- ] — maksymalna wersja włącznie

- ( — minimalna wersja dostępna wyłącznie

- ) — maksymalna wersja dostępna wyłącznie

- Numer pojedynczej wersji — tylko określona wersja

  **Zestaw SDK rozszerzeń** Określa instalację globalną, która nie jest w zakresie określonego produktu i wersji. **Identyfikator platformy docelowej** to platforma docelowa, na przykład "Windows". **Wersja platformy docelowej** to wersja, na przykład 8.0, platformy docelowej. **Nazwa zestawu SDK** i wersja zestawu **SDK** to odpowiednio nazwa i numer wersji zestawu SDK.

  **Ten vsix jest instalowany dla wszystkich użytkowników (wymaga podniesienia uprawnień podczas instalacji)** Jeśli zaznaczysz to pole wyboru, rozszerzenie zostanie zainstalowane dla wszystkich użytkowników. W przeciwnym razie jest instalowany tylko dla bieżącego użytkownika.

  **Ten vsix jest instalowany przez Instalator Windows** Jeśli zaznaczysz to pole wyboru, rozszerzenie zostanie zainstalowane przez Instalator Windows (*.msi* plik ); W przeciwnym razie jest instalowany jako typowy pakiet VSIX *(plik vsix).*

  Karta **Zasoby** zawiera następujące kontrolki.

  **Lista zasobów** Wyświetla listę elementów zawartości opisujących elementy rozszerzenia lub zawartości, które są powierzchnią tego pakietu. Każdy element rozszerzenia lub zawartości jest wymieniony oddzielnie według źródła, typu i ścieżki. Rozszerzenia i elementy zawartości można dodawać do listy, modyfikować i usuwać. Typ i ścieżka rozszerzenia lub elementu zawartości odpowiada i `Type` `Path` atrybuty skojarzonego `Asset` elementu. Znane są następujące typy:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Aby dodać lub edytować element zawartości, należy określić typ zasobu, to czy element zawartości jest projektem w bieżącym rozwiązaniu, czy plikiem w systemie plików, oraz nazwę projektu. Można również określić nazwę folderu, w którym ma zostać osadzony.

  Możesz również tworzyć własne typy i nadawać im unikatowe nazwy.

  Karta **Zależności** zawiera następujące kontrolki.

  **Nazwa, źródło i zakres wersji** Wyświetla listę elementów zależności tego pakietu, które są innymi pakietami, od których zależy ten pakiet. Jeśli określono pakiet zależności, należy go zainstalować przed zainstalowaniem tego pakietu; W przeciwnym razie ten pakiet musi go zainstalować.

  Pakiety zależności są określane według identyfikatora, nazwy, zakresu wersji, źródła i sposobu rozwiązania zależności. Każdy pakiet zależności jest wymieniony oddzielnie według nazwy, wersji i źródła. Pakiety zależności można dodawać do listy, modyfikować i usuwać.

  Identyfikator musi odpowiadać `ID` atrybutowi metadanych pakietu zależności. Źródłem może być projekt w bieżącym rozwiązaniu, aktualnie zainstalowane rozszerzenie lub plik. Ustawienie **Jak jest rozwiązywane zależności** może być ścieżką względną zagnieżdżonych pakietów lub adresem URL lokalizacji pobierania zależności. Identyfikator, wersja i rozwiązanie pakietu zależności odpowiadają atrybutom `Id` `Version` , i `Location` skojarzonego `Dependency` elementu.

## <a name="see-also"></a>Zobacz też
- [Informacje o schemacie rozszerzenia VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
