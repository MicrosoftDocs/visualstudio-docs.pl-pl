---
title: Najważniejsze wskazówki dotyczące wdrażania wtyczki kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740054"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Najważniejsze wskazówki dotyczące wdrażania wtyczki kontroli źródła
Poniższe szczegóły techniczne mogą pomóc w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]niezawodnym zaimplementowanie wtyczki kontroli źródła.

## <a name="memory-management-issues"></a>Problemy z zarządzaniem pamięcią
 W większości przypadków zintegrowane środowisko programistyczne (IDE), który jest wywołującym, zwalnia i przydziela pamięć. Wtyczka formantu źródła zwraca ciągi i inne elementy w buforach przydzielonych przez wywołującego. Wyjątki są odnotowane w opisach określonych funkcji, w których występują.

## <a name="arrays-of-file-names"></a>Tablice nazw plików
 Po przekazaniu tablicy plików nie jest przekazywana jako ciągła tablica nazw plików. Jest przekazywana jako tablica wskaźników do nazw plików. Na przykład w [SccGet](../extensibility/sccget-function.md)nazwy plików są `lpFileNames` przekazywane przez `lpFileNames` parametr, gdzie `char **`jest faktycznie wskaźnik do . `lpFileNames`[0] jest wskaźnikiem do `lpFileNames`imienia, [1] jest wskaźnikiem do drugiej nazwy i tak dalej.

## <a name="large-model"></a>Duży model
 Wszystkie wskaźniki są 32 bity, nawet w 16-bitowych systemach operacyjnych.

## <a name="fully-qualified-paths"></a>W pełni kwalifikowane ścieżki
 W przypadku gdy nazwy plików lub katalogi są określone jako argumenty, muszą to być w pełni kwalifikowane ścieżki lub ścieżki UNC bez kończących ukośników odwrotnych. Jest odpowiedzialny za wtyczkę kontroli źródła, aby przetłumaczyć je na ścieżki względne, jeśli jest to wymaganie podstawowego systemu kontroli źródła.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Określ w pełni kwalifikowaną ścieżkę dla zarejestrowanej biblioteki DLL
 IDE nie ładuje już bibliotek DLL ze ścieżek względnych (na przykład *.\NewProvider.dll*). Należy określić pełną ścieżkę biblioteki DLL (na przykład *C:\Providers\NewProvider.dll*). Ten wymóg zwiększa bezpieczeństwo IDE, zapobiegając załadunku nieautoryzowanych lub personifikowanych bibliotek DLL kontroli źródła.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Sprawdzanie istniejącej wtyczki VSSCI podczas instalowania wtyczki sterowania źródłem
 Użytkownik, który planuje zainstalować wtyczkę kontroli źródła, może mieć już zainstalowaną na komputerze istniejącą wtyczkę kontroli źródła. Program instalacyjny (instalacyjny) dla utworzonej wtyczki powinien określać, czy istnieją istniejące wartości dla odpowiednich kluczy rejestru. Jeśli te klucze są już ustawione, program instalacyjny powinien zapytać użytkownika, czy zarejestrować wtyczkę jako domyślną wtyczkę formantu źródła i zastąpić tę, która jest już zainstalowana.

## <a name="error-result-codes-and-reporting"></a>Kody wyników błędów i raportowanie
 Kod `SCC_OK` zwrotny dla funkcji kontroli źródła wskazuje, że operacja powiodła się dla wszystkich plików. Jeśli operacja nie powiedzie się, oczekuje się, że zwróci ostatni napotkany kod błędu.

 Reguła raportowania jest, że jeśli wystąpi błąd w IDE, IDE jest odpowiedzialny za zgłoszenie go. Jeśli wystąpi błąd w systemie kontroli źródła, wtyczka kontroli źródła jest odpowiedzialna za zgłoszenie go. Na przykład **żadne pliki są obecnie wybrane** będą zgłaszane przez IDE, natomiast ten plik jest już **wyewidencjonowany** będzie zgłaszany przez wtyczkę.

## <a name="the-context-structure"></a>Struktura kontekstu
 Podczas wywołania [SccInitialize](../extensibility/sccinitialize-function.md), wywołujący `ppvContext` przekazuje parametr, który jest niezainicjowany dojście do void. Wtyczka formantu źródła może zignorować ten parametr lub może przydzielić strukturę dowolnego rodzaju i umieścić wskaźnik do tej struktury w przekazanym wskaźnikiem. IDE nie rozumie tej struktury, ale przekazuje wskaźnik do tej struktury do każdego innego wywołania w dodatku plug-in. Zapewnia to cenne informacje pamięci podręcznej kontekstu do wtyczki, które można użyć do obsługi informacji o stanie globalnym, który utrzymuje się między wywołaniami funkcji bez użycia zmiennych globalnych. Wtyczka jest odpowiedzialna za uwolnienie struktury na wezwanie do [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Jeśli dodatek ustawia `SCC_CAP_REENTRANT` bit w [SccInitialize](../extensibility/sccinitialize-function.md) (w szczególności `lpSccCaps` w parametrze), wiele struktur kontekstu są używane do śledzenia wszystkich projektów, które są otwarte.

## <a name="bitflags-and-other-command-options"></a>Bitflags i inne opcje poleceń
 Dla każdego polecenia, takich jak [SccGet](../extensibility/sccget-function.md), IDE można określić wiele opcji, które zmieniają zachowanie polecenia.

 Interfejs API obsługuje ustawienie niektórych opcji `fOptions` przez IDE za pośrednictwem parametru. Opcje te są opisane w [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) wraz z poleceniami, które mają wpływ. Ogólnie rzecz biorąc są to opcje, dla których użytkownik nie zostanie poproszony.

 Większość opcji ustawień konfigurowanych przez użytkownika nie jest zdefiniowana w ten sposób, ponieważ różnią się one znacznie w zależności od wtyczek kontroli źródła. W związku z tym zalecanym mechanizmem jest przycisk **Zaawansowane.** Na przykład w oknie dialogowym **Pobierz** IDE wyświetla tylko informacje, które rozumie, ale wyświetla również przycisk **Zaawansowane,** jeśli wtyczka ma opcje dla tego polecenia. Gdy użytkownik kliknie **przycisk Zaawansowane,** IDE wywołuje [SccGetCommandOptions,](../extensibility/sccgetcommandoptions-function.md) aby włączyć wtyczkę kontroli źródła, aby monitować użytkownika o informacje, takie jak bitflags lub data/godzina. Wtyczka zwraca te informacje w strukturze, która `SccGet` jest przekazywana z powrotem podczas polecenia.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Tworzenie wtyczki formantu źródła](../extensibility/internals/creating-a-source-control-plug-in.md)
