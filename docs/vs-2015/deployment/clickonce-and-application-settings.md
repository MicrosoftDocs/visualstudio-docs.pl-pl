---
title: ClickOnce i ustawienia aplikacji | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696687"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce i ustawienia aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia aplikacji dla formularzy Windows Forms można łatwo tworzyć, przechowywać i Obsługa niestandardowych aplikacji i preferencji użytkowników na komputerze klienckim. Poniższy dokument w tym artykule opisano działanie pliki ustawień aplikacji w aplikacji ClickOnce, i jak ClickOnce wykonuje migrację ustawień, po uaktualnieniu do następnej wersji.  
  
 Poniższe informacje dotyczą tylko w domyślny dostawca ustawień aplikacji, <xref:System.Configuration.LocalFileSettingsProvider> klasy. Jeśli podasz niestandardowego dostawcy, tego dostawcy określi, jak przechowuje swoje dane i jak uaktualni ona jego ustawienia między wersjami. Aby uzyskać więcej informacji na temat dostawców ustawień aplikacji, zobacz [Architektura ustawień aplikacji](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Pliki ustawień aplikacji  
 Ustawienia aplikacji wykorzystuje dwa pliki: *aplikacji*. exe.config i user.config, gdzie *aplikacji* jest nazwą aplikacji Windows Forms. User.config jest tworzony na czas klienta pierwsza aplikacja przechowuje ustawienia z zakresu użytkownika. *Aplikacja*. exe.config, z drugiej strony, będzie istnieć przed ich wdrożeniem zdefiniowania wartości domyślne ustawień. Program Visual Studio będzie zawierać ten plik automatycznie korzystając z jego **Publikuj** polecenia. Jeśli tworzysz aplikację ClickOnce za pomocą Mage.exe lub MageUI.exe, musisz upewnić się, ten plik jest dołączony do aplikacji przez inne pliki podczas wypełniania manifest aplikacji.  
  
 W aplikacjach Windows Forms, nie wdrożone za pomocą technologii ClickOnce, aplikacja firmy *aplikacji*. exe.config plik jest przechowywany w katalogu aplikacji, gdy w pliku user.config znajduje się w jego **Documents and Settings**  folderu. W aplikacji ClickOnce *aplikacji*. exe.config znajduje się w katalogu aplikacji w pamięci podręcznej aplikacji ClickOnce i user.config, który znajduje się w katalogu danych ClickOnce dla tej aplikacji.  
  
 Niezależnie od tego, w jaki sposób wdrażania aplikacji, ustawień aplikacji zapewnia bezpieczny dostęp do odczytu do *aplikacji*. exe.config i bezpieczne odczytu i zapisu do user.config.  
  
 W aplikacji ClickOnce rozmiar pliki konfiguracji używane przez ustawienia aplikacji jest ograniczona przez rozmiar pamięci podręcznej funkcji ClickOnce. Aby uzyskać więcej informacji, zobacz [Przegląd pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Uaktualnienia wersji  
 Tak, jak każda wersja aplikacji ClickOnce jest odizolowana od wszystkich innych wersji, ustawień aplikacji dla aplikacji ClickOnce są odizolowane od ustawień innych wersjach. Po użytkownik uaktualnienia do nowszej wersji aplikacji, ustawień aplikacji porównuje ustawień najnowsze (najwyższym numerze) wersji względem ustawienia dostarczony wraz z zaktualizowaną wersję i scalenia ustawień do nowego zestawu plików ustawień.  
  
 W poniższej tabeli opisano, jak decyduje, ustawienia, które można skopiować ustawienia aplikacji.  
  
|Typ zmiany|Akcja uaktualniania|  
|--------------------|--------------------|  
|Ustawienie, dodane do *aplikacji*. exe.config|Nowe ustawienie zostanie scalona z bieżącą wersją *aplikacji*. exe.config|  
|Ustawienie usunięte z *aplikacji*. exe.config|Stare ustawienie zostanie usunięte z bieżącej wersji *aplikacji*. exe.config|  
|Domyślne ustawienia, które zostały zmienione; Ustawienie lokalne nadal równa oryginalnych wartości domyślnych w user.config|Ustawienie zostanie scalona z wartością user.config bieżącej wersji za pomocą nowego domyślnego|  
|Domyślne ustawienia, które zostały zmienione; Ustawienie wartość do wartości niedomyślnej w user.config|Ustawienie zostanie scalona z bieżącą wersję user.config o wartości innych niż domyślne, przechowywane|  
  
 Jeśli ustawienia aplikacji zostały utworzone klasy otoki i ma zostać dostosowana logika aktualizacji, można zastąpić <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metody.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce i ustawienia roamingu  
 ClickOnce nie działa z ustawień mobilnego dostępu, co pozwala plik ustawień można wykonać na maszynach, w sieci. Jeśli potrzebujesz ustawienia roamingu, należy do implementowania dostawcy ustawień aplikacji, która przechowuje ustawienia za pośrednictwem sieci lub tworzenia własnych klas niestandardowych ustawień do przechowywania ustawień na komputerze zdalnym. Aby uzyskać więcej informacji w dostawców ustawień, zobacz [Architektura ustawień aplikacji](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Przegląd ustawień aplikacji](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Przegląd pamięci podręcznej w technologii ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
