---
title: Określanie programów obsługi plików dla rozszerzeń nazw plików | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699753"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Określanie programów obsługi plików dla rozszerzeń nazw plików
Istnieje kilka sposobów na określenie aplikacji, która obsługuje plik, który ma rozszerzenie określonego pliku. Zlecenia OpenWithList i OpenWithProgids są dwa sposoby określania programów obsługi plików w ramach wpisu rejestru dla rozszerzenia pliku.

## <a name="openwithlist-verb"></a>Zlecenie OpenWithList
 Po kliknięciu prawym przyciskiem myszy pliku w Eksploratorze Windows zobaczysz polecenie **Otwórz** . Jeśli więcej niż jeden produkt jest skojarzony z rozszerzeniem, zobaczysz menu **Otwórz za pomocą** .

 Możesz zarejestrować różne aplikacje, aby otworzyć rozszerzenie przez ustawienie klucza OpenWithList dla rozszerzenia pliku w HKEY_CLASSES_ROOT. Aplikacje wymienione w tym kluczu dla rozszerzenia pliku są wyświetlane w nagłówku **zalecane programy** w oknie dialogowym **Otwórz za pomocą** . Poniższy przykład pokazuje aplikacje zarejestrowane w celu otworzenia rozszerzenia pliku. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Klucze określające aplikacje znajdują się na liście w obszarze HKEY_CLASSES_ROOT \Applications.

 Dodając klucz OpenWithList, deklarujesz, że aplikacja obsługuje rozszerzenie pliku, nawet jeśli inna aplikacja przejmuje własność rozszerzenia. Może to być przyszła wersja aplikacji lub innej aplikacji.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Identyfikatory programistyczne (PROGID) są przyjaznymi wersjami ClassIDs, które identyfikują wersję aplikacji lub obiektu COM. Każdy obiekt, który ma być możliwy do utworzenia, powinien mieć własny identyfikator ProgID. Na przykład VisualStudio. DTE. 7.1 uruchamia program Visual Studio .NET 2003 podczas uruchamiania VisualStudio. DTE. 10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jako właściciel typu projektu lub typu elementu projektu, należy utworzyć specyficzny dla danej wersji identyfikator ProgID dla rozszerzenia pliku. Te identyfikatory ProgID mogą być nadmiarowe w tym, że więcej niż jeden identyfikator ProgID może uruchamiać tę samą aplikację. Aby uzyskać więcej informacji, zobacz [Rejestrowanie czasowników dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md).

 Użyj następującej konwencji nazewnictwa dla ProgID plików z wersjami, aby uniknąć duplikacji z rejestracją od innych dostawców:

|Rozszerzenie pliku|Wersja ProgID|
|--------------------|----------------------|
|. rozszerzenie|ProductName. rozszerzenie. versionMajor. versionMinor|

 Można zarejestrować różne aplikacje, które mogą otworzyć określone rozszerzenie pliku, dodając identyfikatory ProgID jako wartości do HKEY_CLASSES_ROOT \\ *\<extension>* klucza \OpenWithProgids. Ten klucz rejestru zawiera listę alternatywnych identyfikatory ProgID skojarzonych z rozszerzeniem pliku. Aplikacje skojarzone z wymienionymi identyfikatorami ProgID pojawiają się w podmenu **Otwórz za pomocą**_nazwy produktu_ . Jeśli ta sama aplikacja jest określona w `OpenWithList` `OpenWithProgids` kluczach i, system operacyjny Scala duplikaty.

> [!NOTE]
> Ten `OpenWithProgids` klucz jest obsługiwany tylko w systemie Windows XP. Ponieważ inne systemy operacyjne ignorują ten klucz, nie należy używać go jako jedynej rejestracji dla programów obsługi plików. Użyj tego klucza, aby zapewnić lepsze środowisko użytkownika w systemie Windows XP.

 Dodaj żądane identyfikatory ProgID jako wartości typu REG_NONE. Poniższy kod zawiera przykład rejestrowania ProgID dla rozszerzenia pliku (.* EXT*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Identyfikator ProgID określony jako wartość domyślna dla rozszerzenia pliku jest domyślną obsługą plików. W przypadku zmodyfikowania identyfikatora ProgID dla rozszerzenia pliku, który został dostarczony z poprzednią wersją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub który może zostać przejęty przez inne aplikacje, należy zarejestrować `OpenWithProgids` klucz dla rozszerzenia pliku i określić nowy identyfikator ProgID na liście wraz z starymi, które obsługują. Na przykład:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Jeśli stary identyfikator ProgID ma skojarzone z nim czasowniki, te czasowniki również zostaną wyświetlone w obszarze **Otwórz z** *nazwą produktu* w menu skrótów.

## <a name="see-also"></a>Zobacz też
- [Informacje o rozszerzeniach nazw plików](../extensibility/about-file-name-extensions.md)
- [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)
