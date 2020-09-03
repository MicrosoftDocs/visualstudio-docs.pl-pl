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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184136"
---
# <a name="clickonce-and-application-settings"></a>Ustawienia technologii ClickOnce i aplikacji
Ustawienia aplikacji dla Windows Forms ułatwiają tworzenie, przechowywanie i konserwowanie niestandardowych preferencji aplikacji i użytkowników na kliencie. W poniższym dokumencie opisano sposób działania plików ustawień aplikacji w aplikacji ClickOnce oraz sposób migrowania ustawień przez program ClickOnce po uaktualnieniu użytkownika do kolejnej wersji.

 Poniższe informacje dotyczą tylko domyślnego dostawcy ustawień aplikacji, <xref:System.Configuration.LocalFileSettingsProvider> klasy. W przypadku podania dostawcy niestandardowego dostawca określi, w jaki sposób przechowuje swoje dane i w jaki sposób uaktualnia ustawienia między wersjami. Aby uzyskać więcej informacji na temat dostawców ustawień aplikacji, zobacz [Architektura ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Pliki ustawień aplikacji
 Ustawienia aplikacji zużywają dwa pliki: * \<app>.exe.config* i *user.config*, gdzie *App* jest nazwą aplikacji Windows Forms. *user.config* jest tworzony na kliencie przy pierwszym zapisaniu przez aplikację ustawień o zakresie użytkownika. * \<app>.exe.config*, z kolei, będzie istniał przed wdrożeniem, jeśli zdefiniujesz wartości domyślne dla ustawień. Program Visual Studio będzie automatycznie uwzględniał ten plik podczas korzystania z polecenia **Publikuj** . Jeśli tworzysz aplikację ClickOnce przy użyciu *Mage.exe* lub *MageUI.exe*, musisz upewnić się, że ten plik jest dołączony do innych plików aplikacji podczas wypełniania manifestu aplikacji.

 W aplikacji Windows Forms niewdrożonej przy użyciu technologii ClickOnce plik * \<app>.exe.config* aplikacji jest przechowywany w katalogu aplikacji, podczas gdy plik *user.config* jest przechowywany w folderze **dokumenty i ustawienia** użytkownika. W aplikacji ClickOnce * \<app>.exe.config* znajdują się w katalogu aplikacji wewnątrz pamięci podręcznej aplikacji ClickOnce i *user.config* znajdują się w katalogu danych ClickOnce dla tej aplikacji.

 Bez względu na sposób wdrażania aplikacji, ustawienia aplikacji zapewniają bezpieczny dostęp do odczytu do * \<app>.exe.config*i bezpieczny dostęp do odczytu/zapisu do *user.config*.

 W aplikacji ClickOnce rozmiar plików konfiguracji używanych przez ustawienia aplikacji jest ograniczony przez rozmiar pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [Omówienie pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Uaktualnienia wersji
 Podobnie jak każda wersja aplikacji ClickOnce jest odizolowana od wszystkich innych wersji, ustawienia aplikacji dla aplikacji ClickOnce są odizolowane od ustawień dla innych wersji. Po uaktualnieniu użytkownika do nowszej wersji aplikacji ustawienia aplikacji porównuje najnowsze (najwyższe wartości) z ustawieniami dostarczonymi ze zaktualizowaną wersją i scala ustawienia w nowym zestawie plików ustawień.

 W poniższej tabeli opisano sposób, w jaki ustawienia aplikacji decydują o ustawieniach, które należy skopiować.

|Typ zmiany|Akcja uaktualniania|
|--------------------|--------------------|
|Dodano ustawienie do * \<app>.exe.config*|Nowe ustawienie zostanie scalone z * \<app>.exe.config* bieżącej wersji|
|Ustawienie usunięte z * \<app>.exe.config*|Stare ustawienie zostanie usunięte z * \<app>.exe.config* bieżącej wersji|
|Ustawienie domyślne zmiany ustawienia; Ustawienie lokalne nadal ma domyślnie wartość pierwotna w *user.config*|To ustawienie jest scalane w *user.config* bieżącej wersji z nową wartością domyślną jako wartość|
|Ustawienie domyślne zmiany ustawienia; ustawienie wartości innej niż domyślna w *user.config*|To ustawienie jest scalane w *user.config* bieżącej wersji z zachowaną wartością niedomyślną|

Jeśli utworzono własną klasę otoki ustawień aplikacji i chcesz dostosować logikę aktualizacji, możesz przesłonić tę <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodę.

## <a name="clickonce-and-roaming-settings"></a>Ustawienia ClickOnce i roamingu
 Technologia ClickOnce nie działa w przypadku ustawień roamingu, co pozwala plikom ustawień obejść między maszynami w sieci. W przypadku konieczności ustawienia roamingu należy wdrożyć dostawcę ustawień aplikacji, który przechowuje ustawienia w sieci, lub opracować własne klasy ustawień niestandardowych do przechowywania ustawień na komputerze zdalnym. Aby uzyskać więcej informacji na temat dostawców ustawień, zobacz [Architektura ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Przegląd ustawień aplikacji](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Omówienie pamięci podręcznej w technologii ClickOnce](../deployment/clickonce-cache-overview.md)
- [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)