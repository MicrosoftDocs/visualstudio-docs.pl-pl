---
title: Najlepsze rozwiązania dotyczące wdrażania wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99166c8bf9a76deaa3805bfd8f5ac6db35e5c0a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184715"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Najlepsze rozwiązania dotyczące wdrażania wtyczki kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące szczegóły techniczne może pomóc w wiarygodny sposób implementacji wtyczka do kontroli źródła w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="memory-management-issues"></a>Problemy z pamięcią zarządzania  
 W większości przypadków zintegrowanego środowiska programistycznego (IDE), która jest obiekt wywołujący, wersje i przydziela pamięć. Wtyczka do kontroli źródła zwraca ciągów i innych elementów bufory przypisane do obiektu wywołującego. Wyjątki są zaznaczone w opisach określonych funkcji, w którym wystąpią.  
  
## <a name="arrays-of-file-names"></a>Tablice o nazwach plików  
 Po upływie tablicę plików nie jest przekazywany jako ciągły tablica nazw plików. Jest przekazywany jako tablicę wskaźników do nazw plików. Na przykład w [SccGet](../extensibility/sccget-function.md), nazwy plików są przekazywane przez `lpFileNames` parametru, gdzie `lpFileNames` jest właściwie wskaźnikiem do `char **`. `lpFileNames`[0] jest wskaźnikiem do imienia, `lpFileNames`[1] jest wskaźnikiem do drugiej i tak dalej.  
  
## <a name="large-model"></a>Modele o dużych  
 Wszystkie wskaźniki są 32-bitowy, nawet w przypadku 16-bitowych systemach operacyjnych.  
  
## <a name="fully-qualified-paths"></a>W pełni kwalifikowane ścieżki  
 Gdy nazwy plików lub katalogów są określane jako argumentów, muszą być w pełni kwalifikowanej ścieżki lub ścieżek UNC, bez końcowej ukośników odwrotnych. Jest odpowiedzialny za wtyczka do kontroli źródła do translacji je do ścieżek względnych w przypadku oznacza to wymaganie bazowego systemu kontroli źródła.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Określ w pełni kwalifikowana ścieżka dla zarejestrowanej biblioteki DLL  
 IDE nie będzie już ładować biblioteki DLL ze ścieżek względnych (na przykład.\NewProvider.dll). (Na przykład C:\Providers\NewProvider.dll) należy określić pełną ścieżkę pliku DLL. To wymaganie wzmacnia zabezpieczenia środowiska IDE poprzez uniemożliwienie ładowanie kontroli źródła nieautoryzowani lub spersonifikowanego biblioteki dll.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Sprawdzaj istniejące VSSCI wtyczki po zainstalowaniu wtyczka do kontroli źródła  
 Użytkownik zamierza zainstalować wtyczkę kontroli źródła może już istnieć istniejących wtyczka do kontroli źródła zainstalowany na komputerze. Program instalacyjny (Instalatora) dla wtyczki, należy utworzyć należy ustalić, czy są istniejące wartości kluczy rejestru odpowiednich. Jeśli te klucze są już skonfigurowane, program instalacyjny należy poprosić użytkownika czy zarejestrować wtyczkę jako domyślnego dodatku plug-in kontroli źródła, a następnie Zastąp ten, który jest już zainstalowana.  
  
## <a name="error-result-codes-and-reporting"></a>Kody wyników programu błąd i raportowanie  
 `SCC_OK` Zwracają kod funkcji kontroli źródła wskazuje, czy operacja powiodła się dla wszystkich plików. Jeśli operacja zakończy się niepowodzeniem, oczekuje się, aby zwrócić kod ostatniego błędu.  
  
 Reguły dla raportowania jest, że w przypadku wystąpienia błędu w środowisku IDE, IDE jest odpowiedzialny za zgłoszenie go. Jeśli wystąpi błąd w systemie kontroli źródła, wtyczka do kontroli źródła jest odpowiedzialny za zgłoszenie go. Na przykład "żadne pliki nie są obecnie wybrane" będzie raportowane przez środowisko IDE, "ten plik został już wyewidencjonowany" będzie zgłoszone przez wtyczkę.  
  
## <a name="the-context-structure"></a>Struktura kontekstu  
 Podczas wywołania [SccInitialize](../extensibility/sccinitialize-function.md), obiekt wywołujący przekazuje `ppvContext` parametr, który jest niezainicjowany uchwyt do void. Wtyczka do kontroli źródła można zignorować ten parametr, lub można przydzielić struktury dowolnego rodzaju i umieścić wskaźnik do tej struktury w przekazanych wskaźnika. IDE nie rozpoznaje tej struktury, ale przekazuje wskaźnik do tej struktury do każdego innego wywołania we wtyczce. Zawiera informacje o pamięci podręcznej kontekstu przydatne do wtyczki, może użyć do zarządzania danymi stan globalny, trwające we wszystkich wywołaniach funkcji bez używania zmiennych globalnych. Dodatek jest odpowiedzialny za zwalnianie struktury w wywołaniu [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Jeśli wtyczka ustawia `SCC_CAP_REENTRANT` bit w [SccInitialize](../extensibility/sccinitialize-function.md) (w szczególności w `lpSccCaps` parametru), wiele struktur kontekstu są używane do śledzenia projektów, które są otwarte.  
  
## <a name="bitflags-and-other-command-options"></a>Flagi bitowe i inne opcje polecenia  
 Dla każdego polecenia takie jak [SccGet](../extensibility/sccget-function.md), środowiska IDE można określić wiele opcji, które zmieniają zachowanie polecenia.  
  
 Interfejs API obsługuje ustawienie pewnych opcji IDE za pośrednictwem `fOptions` parametru. Te opcje są opisane w [flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) wraz z poleceniami, które wpływają. Ogólnie rzecz biorąc są to opcje, dla których użytkownik nie otrzyma monitu.  
  
 Najbardziej konfigurowanych przez użytkownika opcji ustawienia nie są zdefiniowane w ten sposób, ponieważ są bardzo zróżnicowane między wtyczek kontroli kodu źródłowego. Dlatego jest zalecane mechanizm **zaawansowane** przycisku. Na przykład w **uzyskać** okno dialogowe, środowisko IDE wyświetla tylko te informacje, które sam, ale jest również wyświetlana **zaawansowane** przycisk, jeśli dodatek udostępnia opcji dla tego polecenia. Kiedy użytkownik kliknie **zaawansowane** przycisk wywołania IDE [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) umożliwiające wtyczka do kontroli źródła na monitowanie użytkownika o informacje, takie jak flagi bitowe lub daty/godziny. Wtyczka ta informacja jest zwracana w strukturze, który jest przekazywany w trakcie `SccGet` polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)
