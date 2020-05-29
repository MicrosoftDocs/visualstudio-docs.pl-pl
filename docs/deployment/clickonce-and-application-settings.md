---
title: Ustawienia ClickOnce i aplikacje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a72b5bc3f3645d9af1008f2c178ab285e8b45449
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184136"
---
# <a name="clickonce-and-application-settings"></a>Ustawienia technologii ClickOnce i aplikacji
Ustawienia aplikacji dla Windows Forms ułatwiają tworzenie, przechowywanie i konserwowanie niestandardowych preferencji aplikacji i użytkowników na kliencie. W poniższym dokumencie opisano sposób działania plików ustawień aplikacji w aplikacji ClickOnce oraz sposób migrowania ustawień przez program ClickOnce po uaktualnieniu użytkownika do kolejnej wersji.

 Poniższe informacje dotyczą tylko domyślnego dostawcy ustawień aplikacji, <xref:System.Configuration.LocalFileSettingsProvider> klasy. W przypadku podania dostawcy niestandardowego dostawca określi, w jaki sposób przechowuje swoje dane i w jaki sposób uaktualnia ustawienia między wersjami. Aby uzyskać więcej informacji na temat dostawców ustawień aplikacji, zobacz [Architektura ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Pliki ustawień aplikacji
 Ustawienia aplikacji zużywają dwa pliki: * \<app> . exe. config* i *User. config*, gdzie *App* to nazwa aplikacji Windows Forms. *plik user. config* jest tworzony na kliencie przy pierwszym użyciu ustawień o zakresie użytkownika. plik * \<app> . exe. config*, z kolei, będzie istniał przed wdrożeniem, jeśli zdefiniujesz wartości domyślne dla ustawień. Program Visual Studio będzie automatycznie uwzględniał ten plik podczas korzystania z polecenia **Publikuj** . Jeśli tworzysz aplikację ClickOnce przy użyciu programu *Mage. exe* lub *MageUI. exe*, musisz upewnić się, że ten plik jest dołączony do innych plików aplikacji podczas wypełniania manifestu aplikacji.

 W aplikacji Windows Forms niewdrożonej przy użyciu technologii ClickOnce plik * \<app> . config* aplikacji jest przechowywany w katalogu aplikacji, natomiast plik *User. config* jest przechowywany w folderze **Documents and Settings** użytkownika. W aplikacji ClickOnce plik * \<app> . exe. config* znajduje się w katalogu aplikacji wewnątrz pamięci podręcznej aplikacji ClickOnce, a *plik user. config* znajduje się w katalogu danych ClickOnce dla tej aplikacji.

 Bez względu na sposób wdrażania aplikacji, ustawienia aplikacji zapewniają bezpieczny dostęp do odczytu do * \<app> pliku exe. config*oraz bezpieczny dostęp do odczytu/zapisu do *pliku User. config*.

 W aplikacji ClickOnce rozmiar plików konfiguracji używanych przez ustawienia aplikacji jest ograniczony przez rozmiar pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [Omówienie pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Uaktualnienia wersji
 Podobnie jak każda wersja aplikacji ClickOnce jest odizolowana od wszystkich innych wersji, ustawienia aplikacji dla aplikacji ClickOnce są odizolowane od ustawień dla innych wersji. Po uaktualnieniu użytkownika do nowszej wersji aplikacji ustawienia aplikacji porównuje najnowsze (najwyższe wartości) z ustawieniami dostarczonymi ze zaktualizowaną wersją i scala ustawienia w nowym zestawie plików ustawień.

 W poniższej tabeli opisano sposób, w jaki ustawienia aplikacji decydują o ustawieniach, które należy skopiować.

|Typ zmiany|Akcja uaktualniania|
|--------------------|--------------------|
|Dodano ustawienie do * \<app> pliku exe. config*|Nowe ustawienie zostanie scalone z bieżącą wersją * \<app> pliku. exe. config*|
|Ustawienie usunięte z * \<app> pliku. exe. config*|Stare ustawienie zostanie usunięte z bieżącej wersji * \<app> . exe. config*|
|Ustawienie domyślne zmiany ustawienia; Ustawienie lokalne nadal ustawia oryginalne domyślne w *pliku User. config*|To ustawienie zostanie scalone z elementem *User. config* bieżącej wersji z nową wartością domyślną jako wartość|
|Ustawienie domyślne zmiany ustawienia; ustawienie wartości innej niż domyślna w *pliku User. config*|To ustawienie zostanie scalone z wartością *User. config* bieżącej wersji, która jest zachowywana.|

Jeśli utworzono własną klasę otoki ustawień aplikacji i chcesz dostosować logikę aktualizacji, możesz przesłonić tę <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodę.

## <a name="clickonce-and-roaming-settings"></a>Ustawienia ClickOnce i roamingu
 Technologia ClickOnce nie działa w przypadku ustawień roamingu, co pozwala plikom ustawień obejść między maszynami w sieci. W przypadku konieczności ustawienia roamingu należy wdrożyć dostawcę ustawień aplikacji, który przechowuje ustawienia w sieci, lub opracować własne klasy ustawień niestandardowych do przechowywania ustawień na komputerze zdalnym. Aby uzyskać więcej informacji na temat dostawców ustawień, zobacz [Architektura ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Przegląd ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Omówienie pamięci podręcznej w technologii ClickOnce](../deployment/clickonce-cache-overview.md)
- [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)