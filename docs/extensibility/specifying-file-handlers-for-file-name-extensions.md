---
title: Określanie programów obsługi plików dla rozszerzeń nazw plików | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699753"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Określanie programów obsługi plików dla rozszerzeń nazw plików
Istnieje wiele sposobów, aby określić aplikację, która obsługuje plik, który ma określone rozszerzenie pliku. Zlecenia OpenWithList i OpenWithProgids to dwa sposoby określania programów obsługi plików pod wpisem rejestru dla rozszerzenia pliku.

## <a name="openwithlist-verb"></a>Czasownik OpenWithList
 Po kliknięciu prawym przyciskiem myszy pliku w Eksploratorze Windows zostanie wyświetlenie polecenia **Otwórz.** Jeśli z rozszerzeniem jest skojarzone więcej niż jeden produkt, zostanie wyświetlone podmenu **Otwórz z.**

 Możesz zarejestrować różne aplikacje, aby otworzyć rozszerzenie, ustawiając klucz OpenWithList dla rozszerzenia pliku w HKEY_CLASSES_ROOT. Aplikacje wymienione pod tym kluczem dla rozszerzenia pliku są wyświetlane w nagłówku **Zalecane programy** w oknie dialogowym **Otwieranie z.** Poniższy przykład przedstawia aplikacje zarejestrowane w celu otwarcia rozszerzenia pliku .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Klucze określające aplikacje pochodzą z listy w obszarze HKEY_CLASSES_ROOT\Applications.

 Dodając klucz OpenWithList, deklarujesz, że aplikacja obsługuje rozszerzenie pliku, nawet jeśli inna aplikacja przejmuje na własność rozszerzenia. Może to być przyszła wersja aplikacji lub innej aplikacji.

## <a name="openwithprogids"></a>Openwithprogids
 Identyfikatory programowe (ProgID) są przyjaznymi wersjami classidów identyfikujących wersję aplikacji lub obiektu COM. Każdy obiekt współtworzylny powinien mieć swój własny identyfikator progid. Na przykład visualstudio.DTE.7.1 uruchamia program Visual Studio .NET 2003 podczas uruchamiania programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VisualStudio.DTE.10.0. Jako właściciel typu projektu lub typu elementu projektu należy utworzyć identyfikator progid specyficzny dla wersji dla rozszerzenia pliku. Te progids może być zbędne w tym więcej niż jeden ProgID może uruchomić tę samą aplikację. Aby uzyskać więcej informacji, zobacz [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md).

 Użyj następującej konwencji nazewnictwa dla wersji progidów plików, aby uniknąć powielania z rejestracją od innych dostawców:

|Rozszerzenie pliku|ProgID wersjonowany|
|--------------------|----------------------|
|.extension|Productname. extension.versionMajor.versionMinor|

 Można zarejestrować różne aplikacje, które są w stanie otworzyć określone rozszerzenie pliku, dodając\\wersjonowane progidy jako wartości do*\<HKEY_CLASSES_ROOT rozszerzenia>* klucza \OpenWithProgids. Ten klucz rejestru zawiera listę alternatywnych progidów skojarzonych z rozszerzeniem pliku. Aplikacje skojarzone z wymienionymi progidami są wyświetlane w podmenu **Otwórz z**_nazwą produktu._ Jeśli ta sama aplikacja jest `OpenWithList` `OpenWithProgids` określona w kluczach i kluczach, system operacyjny scala duplikaty.

> [!NOTE]
> Klucz `OpenWithProgids` jest obsługiwany tylko w systemie Windows XP. Ponieważ inne systemy operacyjne ignorują ten klucz, nie należy używać go jako jedynej rejestracji dla programów obsługi plików. Ten klucz umożliwia lepsze środowisko użytkownika w systemie Windows XP.

 Dodaj żądane progidy jako wartości typu REG_NONE. Poniższy kod zawiera przykład rejestrowania progidów dla rozszerzenia pliku (.* wew.*

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 ProgID określony jako wartość domyślna dla rozszerzenia pliku jest domyślny program obsługi plików. Jeśli zmodyfikujesz ProgID dla rozszerzenia pliku, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który jest dostarczany z poprzednią wersją lub `OpenWithProgids` które mogą zostać przejęte przez inne aplikacje, należy zarejestrować klucz dla rozszerzenia pliku i określić nowy progid na liście wraz ze starymi progidami, które obsługujesz. Przykład:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Jeśli stary ProgID ma z nim skojarzone zlecenia, te zlecenia pojawią się również w obszarze **Otwórz z** *nazwą produktu* w menu skrótów.

## <a name="see-also"></a>Zobacz też
- [Informacje o rozszerzeniach nazw plików](../extensibility/about-file-name-extensions.md)
- [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)
