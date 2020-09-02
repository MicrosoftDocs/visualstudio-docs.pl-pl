---
title: Ustawienia ClickOnce i aplikacje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696687"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce i ustawienia aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia aplikacji dla Windows Forms ułatwiają tworzenie, przechowywanie i konserwowanie niestandardowych preferencji aplikacji i użytkowników na kliencie. W poniższym dokumencie opisano sposób działania plików ustawień aplikacji w aplikacji ClickOnce oraz sposób migrowania ustawień przez program ClickOnce po uaktualnieniu użytkownika do kolejnej wersji.  
  
 Poniższe informacje dotyczą tylko domyślnego dostawcy ustawień aplikacji, <xref:System.Configuration.LocalFileSettingsProvider> klasy. W przypadku podania dostawcy niestandardowego dostawca określi, w jaki sposób przechowuje swoje dane i w jaki sposób uaktualnia ustawienia między wersjami. Aby uzyskać więcej informacji na temat dostawców ustawień aplikacji, zobacz [Architektura ustawień aplikacji](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Pliki ustawień aplikacji  
 Ustawienia aplikacji zużywają dwa pliki: *app*.exe.config i user.config, gdzie *App* to nazwa aplikacji Windows Forms. user.config jest tworzony na kliencie przy pierwszym zapisaniu przez aplikację ustawień o zakresie użytkownika. w przypadku zdefiniowania wartości domyślnych dla ustawień w *aplikacji*.exe.config, które różnią się, będą istnieć przed wdrożeniem. Program Visual Studio będzie automatycznie uwzględniał ten plik podczas korzystania z polecenia **Publikuj** . Jeśli tworzysz aplikację ClickOnce przy użyciu Mage.exe lub MageUI.exe, musisz upewnić się, że ten plik jest dołączony do innych plików aplikacji podczas wypełniania manifestu aplikacji.  
  
 W przypadku aplikacji Windows Forms niewdrożonych przy użyciu technologii ClickOnce plik.exe.config *aplikacji* aplikacji jest przechowywany w katalogu aplikacji, podczas gdy plik user.config jest przechowywany w folderze **dokumenty i ustawienia** użytkownika. W *aplikacji ClickOnce aplikacja.exe.config znajduje* się w katalogu aplikacji wewnątrz pamięci podręcznej aplikacji ClickOnce i user.config znajduje się w katalogu danych ClickOnce dla tej aplikacji.  
  
 Bez względu na sposób wdrażania aplikacji, ustawienia aplikacji zapewniają bezpieczny dostęp do odczytu do *aplikacji*.exe.config i bezpieczny dostęp do odczytu/zapisu do user.config.  
  
 W aplikacji ClickOnce rozmiar plików konfiguracji używanych przez ustawienia aplikacji jest ograniczony przez rozmiar pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [Omówienie pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Uaktualnienia wersji  
 Podobnie jak każda wersja aplikacji ClickOnce jest odizolowana od wszystkich innych wersji, ustawienia aplikacji dla aplikacji ClickOnce są odizolowane od ustawień dla innych wersji. Po uaktualnieniu użytkownika do nowszej wersji aplikacji ustawienia aplikacji porównuje najnowsze (najwyższe wartości) z ustawieniami dostarczonymi ze zaktualizowaną wersją i scala ustawienia w nowym zestawie plików ustawień.  
  
 W poniższej tabeli opisano sposób, w jaki ustawienia aplikacji decydują o ustawieniach, które należy skopiować.  
  
|Typ zmiany|Akcja uaktualniania|  
|--------------------|--------------------|  
|Dodano ustawienie do.exe.config *aplikacji*|Nowe ustawienie zostanie scalone z *aplikacją* bieżącej wersji.exe.config|  
|Ustawienie usunięte z.exe.config *aplikacji*|Stare ustawienie zostanie usunięte z *aplikacji* bieżącej wersji.exe.config|  
|Ustawienie domyślne zmiany ustawienia; Ustawienie lokalne nadal ma domyślnie wartość pierwotna w user.config|To ustawienie jest scalane w user.config bieżącej wersji z nową wartością domyślną jako wartość|  
|Ustawienie domyślne zmiany ustawienia; ustawienie wartości innej niż domyślna w user.config|To ustawienie jest scalane w user.config bieżącej wersji z zachowaną wartością niedomyślną|  
  
 Jeśli utworzono własną klasę otoki ustawień aplikacji i chcesz dostosować logikę aktualizacji, możesz przesłonić tę <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodę.  
  
## <a name="clickonce-and-roaming-settings"></a>Ustawienia ClickOnce i roamingu  
 Technologia ClickOnce nie działa w przypadku ustawień roamingu, co pozwala plikom ustawień obejść między maszynami w sieci. W przypadku konieczności ustawienia roamingu należy wdrożyć dostawcę ustawień aplikacji, który przechowuje ustawienia w sieci, lub opracować własne klasy ustawień niestandardowych do przechowywania ustawień na komputerze zdalnym. Aby uzyskać więcej informacji na temat dostawców ustawień, zobacz [Architektura ustawień aplikacji](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Przegląd ustawień aplikacji](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Omówienie pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
