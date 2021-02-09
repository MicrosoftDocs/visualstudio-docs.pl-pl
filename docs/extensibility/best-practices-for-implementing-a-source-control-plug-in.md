---
title: Implementowanie wtyczki kontroli źródła — najlepsze rozwiązania
description: Przejrzyj te szczegóły techniczne, aby pomóc w niezawodnej implementacji wtyczki kontroli źródła w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80a944c077d520d6d9ecac9557179311ecf20281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893077"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Najlepsze rozwiązania dotyczące implementowania wtyczki kontroli źródła
Poniższe szczegóły techniczne mogą pomóc w niezawodnym wdrożeniu wtyczki kontroli źródła w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Problemy z zarządzaniem pamięcią
 W większości przypadków zintegrowane środowisko programistyczne (IDE), które jest obiektem wywołującym, zwalnia i przydziela pamięć. Wtyczka do kontroli źródła zwraca ciągi i inne elementy w buforach przyznanych przez obiekt wywołujący. Wyjątki są zanotowane w opisach konkretnych funkcji, w których występują.

## <a name="arrays-of-file-names"></a>Tablice nazw plików
 Po przekazaniu tablicy plików nie jest ona przenoszona jako ciągła Tablica nazw plików. Jest ona przenoszona jako tablica wskaźników do nazw plików. Na przykład w [SccGet](../extensibility/sccget-function.md)nazwy plików są przesyłane przez `lpFileNames` parametr, gdzie `lpFileNames` jest w rzeczywistości wskaźnikiem do `char **` . `lpFileNames`[0] jest wskaźnikiem do pierwszej nazwy, `lpFileNames` [1] jest wskaźnikiem do drugiej nazwy i tak dalej.

## <a name="large-model"></a>Duży model
 Wszystkie wskaźniki są 32 bity, nawet w 16-bitowych systemach operacyjnych.

## <a name="fully-qualified-paths"></a>W pełni kwalifikowane ścieżki
 Gdzie nazwy plików lub katalogi są określone jako argumenty, muszą one być w pełni kwalifikowanymi ścieżkami lub ścieżkami UNC bez końcowych ukośników odwrotnych. Jest odpowiedzialna za wtyczkę kontroli źródła, aby przetłumaczyć je na ścieżki względne, jeśli jest to wymaganie bazowego systemu kontroli źródła.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Określ w pełni kwalifikowaną ścieżkę dla zarejestrowanej biblioteki DLL
 IDE nie ładuje już bibliotek DLL ze ścieżek względnych (na przykład *.\NewProvider.dll*). Należy określić pełną ścieżkę do biblioteki DLL (na przykład *C:\Providers\NewProvider.dll*). Ten wymóg wzmacnia zabezpieczenia środowiska IDE, uniemożliwiając ładowanie nieautoryzowanych lub personifikowanych bibliotek DLL kontroli źródła.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Sprawdź obecność istniejącej wtyczki VSSCI podczas instalowania wtyczki kontroli źródła
 Użytkownik, który planuje zainstalować wtyczkę kontroli źródła, może mieć zainstalowaną na komputerze już istniejącą wtyczkę kontroli źródła. Program instalacyjny (Instalator) dla wtyczki, którą tworzysz, powinien określić, czy istnieją wartości dla odpowiednich kluczy rejestru. Jeśli te klucze zostały już ustawione, program instalacyjny powinien polecić użytkownikowi, czy ma zostać zarejestrowana wtyczka jako domyślna Wtyczka kontroli źródła, i zastąpić ten, który jest już zainstalowany.

## <a name="error-result-codes-and-reporting"></a>Kody wyników błędów i raportowanie
 `SCC_OK`Kod powrotny dla funkcji kontroli źródła wskazuje, że operacja powiodła się dla wszystkich plików. Jeśli operacja nie powiedzie się, oczekiwano zwrócenia ostatniego kodu błędu.

 Reguła raportowania polega na tym, że jeśli w środowisku IDE wystąpi błąd, IDE jest odpowiedzialny za zgłaszanie go. W przypadku wystąpienia błędu w systemie kontroli źródła Wtyczka kontroli źródła jest odpowiedzialna za zgłoszenie go. Na przykład **żadne pliki nie są obecnie wybrane** przez IDE, podczas gdy **ten plik jest już wyewidencjonowany** przez wtyczkę.

## <a name="the-context-structure"></a>Struktura kontekstu
 Podczas wywołania do [SccInitialize](../extensibility/sccinitialize-function.md), obiekt wywołujący przekazuje `ppvContext` parametr, który jest niezainicjowanym dojściem do typu void. Wtyczka do kontroli źródła może zignorować ten parametr lub może przydzielić strukturę dowolnego rodzaju i umieścić wskaźnik do tej struktury w przekazanym wskaźniku. IDE nie rozumie tej struktury, ale przekazuje wskaźnik do tej struktury w każdym innym wywołaniu wtyczki. Zapewnia to cenne informacje o pamięci podręcznej kontekstu do wtyczki, która może być używana do przechowywania globalnych informacji o stanie, które utrzymują się w wywołaniach funkcji bez używania zmiennych globalnych. Wtyczka jest odpowiedzialna za zwolnienie struktury w wywołaniu [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Jeśli wtyczka ustawia `SCC_CAP_REENTRANT` bit w [SccInitialize](../extensibility/sccinitialize-function.md) (w szczególnych `lpSccCaps` parametrach), do śledzenia wszystkich otwartych projektów są używane wiele struktur kontekstu.

## <a name="bitflags-and-other-command-options"></a>Bitflags i inne opcje polecenia
 Dla każdego polecenia, takiego jak [SccGet](../extensibility/sccget-function.md), IDE może określić wiele opcji, które zmieniają zachowanie polecenia.

 Interfejs API obsługuje ustawienie niektórych opcji przez środowisko IDE za pomocą `fOptions` parametru. Te opcje są opisane w [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) wraz z poleceniami, które mają wpływ na. Ogólnie rzecz biorąc, są to opcje, dla których użytkownik nie zostanie monitowany.

 Większość konfigurowalnych opcji ustawień użytkownika nie jest zdefiniowana w ten sposób, ponieważ różnią się one między wtyczkami kontroli źródła. W związku z tym zalecanym mechanizmem jest przycisk **Zaawansowane** . Na przykład w oknie dialogowym **pobieranie** środowisko IDE wyświetla tylko informacje, które rozumie, ale również wyświetla przycisk **Zaawansowane** , jeśli wtyczka zawiera opcje dla tego polecenia. Gdy użytkownik kliknie przycisk **Zaawansowane** , IDE wywołuje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) , aby włączyć wtyczkę kontroli źródła w celu wyświetlenia monitu o podanie informacji, takich jak bitflags lub Data/godzina. Wtyczka zwraca te informacje w strukturze, która jest przenoszona z powrotem podczas wykonywania `SccGet` polecenia.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Tworzenie wtyczki kontroli źródła](../extensibility/internals/creating-a-source-control-plug-in.md)
