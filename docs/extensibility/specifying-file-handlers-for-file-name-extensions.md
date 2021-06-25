---
title: Określanie programów obsługi plików dla rozszerzeń nazw plików | Microsoft Docs
description: Dowiedz się, jak określić, która aplikacja obsługuje rozszerzenie pliku w zestawie SDK Visual Studio za pomocą openWithList i OpenWithProgids.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab370b4be8c12ad0df0c4822bcc7b487fb4aa21
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899449"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Określanie programów obsługi plików dla rozszerzeń nazw plików
Istnieje wiele sposobów określania aplikacji, która obsługuje plik, który ma konkretne rozszerzenie pliku. Czasowniki OpenWithList i OpenWithProgids to dwa sposoby określania programów obsługi plików w obszarze wpisu rejestru dla rozszerzenia pliku.

## <a name="openwithlist-verb"></a>Czasownik OpenWithList
 Po kliknięciu prawym przyciskiem myszy pliku w Eksplorator Windows zostanie wyświetlony **otwórz** polecenia. Jeśli z rozszerzeniem jest skojarzony więcej niż jeden produkt, zostanie wyświetlony podmenu **Otwórz** za pomocą.

 Możesz zarejestrować różne aplikacje, aby otworzyć rozszerzenie, ustawiając klucz OpenWithList dla rozszerzenia pliku w HKEY_CLASSES_ROOT. Aplikacje wymienione pod tym kluczem rozszerzenia pliku są wyświetlane pod nagłówkiem **Zalecane programy** w **oknie dialogowym Otwórz** za pomocą. W poniższym przykładzie pokazano aplikacje zarejestrowane w celu otwarcia rozszerzenia pliku .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Klucze określające aplikacje znajdują się na liście w obszarze HKEY_CLASSES_ROOT\Applications.

 Dodając klucz OpenWithList, deklarujesz, że aplikacja obsługuje rozszerzenie pliku, nawet jeśli inna aplikacja przejmuje na własność rozszerzenie. Może to być przyszła wersja aplikacji lub inna aplikacja.

## <a name="openwithprogids"></a>Openwithprogids
 Identyfikatory programowe (ProgID) to przyjazne wersje identyfikatorów ClassID, które identyfikują wersję aplikacji lub obiektu COM. Każdy obiekt współtworzeni powinien mieć własny identyfikator ProgID. Na przykład plik VisualStudio.DTE.7.1 rozpoczyna się Visual Studio .NET 2003 r., a VisualStudio.DTE.10.0 uruchamia program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jako właściciel typu projektu lub typu elementu projektu musisz utworzyć identyfikator ProgID specyficzny dla wersji dla rozszerzenia pliku. Te progidy mogą być nadmiarowe w tym, że więcej niż jeden identyfikator ProgID może uruchomić tę samą aplikację. Aby uzyskać więcej informacji, [zobacz Registering Verbs for File Name Extensions](../extensibility/registering-verbs-for-file-name-extensions.md)(Rejestrowanie zleceń dla rozszerzeń nazw plików).

 Użyj następującej konwencji nazewnictwa dla progów plików wersji, aby uniknąć duplikowania rejestracji od innych dostawców:

|Rozszerzenie pliku|Identyfikator ProgID z wersją|
|--------------------|----------------------|
|Rozszerzenie .extension|Productname. extension.versionMajor.versionMinor|

 Możesz zarejestrować różne aplikacje, które są w stanie otworzyć konkretne rozszerzenie pliku, dodając wartości progid z wersją do klucza HKEY_CLASSES_ROOT \\ *\<extension>* \OpenWithProgids. Ten klucz rejestru zawiera listę alternatywnych progid skojarzonych z rozszerzeniem pliku. Aplikacje skojarzone z wymienionymi progami są wyświetlane w podmenu **Otwórz** za _pomocą_ nazwy produktu. Jeśli ta sama aplikacja jest określona w `OpenWithList` kluczach i `OpenWithProgids` , system operacyjny scala duplikaty.

> [!NOTE]
> Klucz `OpenWithProgids` jest obsługiwany tylko w systemie Windows XP. Ponieważ inne systemy operacyjne ignorują ten klucz, nie należy używać go jako jedynej rejestracji dla programów obsługi plików. Użyj tego klucza, aby zapewnić lepsze środowisko użytkownika w systemie Windows XP.

 Dodaj żądane progidy jako wartości typu REG_NONE. Poniższy kod zawiera przykład rejestrowania progidów dla rozszerzenia pliku (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Identyfikator ProgID określony jako wartość domyślna rozszerzenia pliku jest domyślnym programem obsługi plików. W przypadku zmodyfikowania identyfikatora ProgID dla rozszerzenia pliku dostarczonego z poprzednią wersją programu lub, który może zostać przejmowany przez inne aplikacje, należy zarejestrować klucz rozszerzenia pliku i określić nowy identyfikator ProgID na liście wraz ze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `OpenWithProgids` starymi progami, które obsługujesz. Na przykład:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Jeśli stary identyfikator ProgID ma skojarzone z nim czasowniki, te czasowniki będą również wyświetlane w obszarze **Otwórz** za pomocą *nazwy* produktu w menu skrótów.

## <a name="see-also"></a>Zobacz też
- [Informacje o rozszerzeniach nazw plików](../extensibility/about-file-name-extensions.md)
- [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)
