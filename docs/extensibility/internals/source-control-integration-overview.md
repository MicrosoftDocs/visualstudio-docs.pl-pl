---
title: Omówienie integracji kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705124"
---
# <a name="source-control-integration-overview"></a>Omówienie integracji kontroli kodu źródłowego
W tej sekcji porównano dwa sposoby integracji z kontrolą źródła programu Visual Studio; Wtyczka do kontroli źródła i pakietu VSPackage, które udostępniają rozwiązanie kontroli źródła i podświetlą nowe funkcje kontroli źródła. Program Visual Studio umożliwia ręczne przełączenie między elementami pakietów VSPackage kontroli źródła a wtyczkami kontroli źródła a również automatycznym przełączaniem opartym na rozwiązaniach.

## <a name="source-control-integration"></a>Integracja kontroli źródła
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje dwa typy opcji integracji kontroli źródła. We wszystkich wersjach programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można nadal zintegrować wtyczkę opartą na interfejsie API wtyczki kontroli źródła (wcześniej określanym również jako interfejs API MSSCCI), która zapewnia podstawowe funkcje kontroli źródła przy użyciu interfejsu użytkownika kontroli źródła programu Visual Studio. Z drugiej strony pakietu VSPackage kontroli źródła zapewnia nową ścieżkę głębokiej integracji [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] odpowiednią dla integracji kontroli źródła, która wymaga wysokiego poziomu złożoności i autonomii w modelu kontroli źródła.

 ![Przegląd kontroli źródła](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Wtyczka kontroli źródła
 Wszystkie wersje programu Visual Studio obsługują specyfikację API wtyczki kontroli źródła w wersji 1,2 jako ścieżkę integracji. Implementacja wtyczki kontroli źródła zapisuje plik DLL, który implementuje funkcje interfejsu API wtyczki kontroli źródła dla integracji kontroli źródła i rejestracji zgodnie z opisem w temacie [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md). W tym podejściu zintegrowane środowisko programistyczne (IDE) używa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika dla okien dialogowych, takich jak ewidencjonowanie, wyewidencjonowywanie, narzędzia/opcje właściwości, paski narzędzi i symbole kontroli źródła. Ścisła zgodność z interfejsem API kontroli źródła zapewnia łatwą integrację z programem Visual Studio i bezpłatnym użytkownikom. Oznacza to, że wtyczka do kontroli źródła musi zaimplementować większość funkcji i wywołań zwrotnych szczegółowych w interfejsie API.

 Aby zaimplementować wtyczkę kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, wykonaj następujące kroki:

1. Utwórz bibliotekę DLL, która implementuje funkcje określone w [wtyczkach kontroli źródła](../../extensibility/source-control-plug-ins.md).

2. Zarejestruj bibliotekę DLL, wprowadzając odpowiednie wpisy rejestru (opisane w artykule [jak zainstalować wtyczkę kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Tworzenie interfejsu użytkownika pomocnika i wyświetlanie monitu o pakiet adaptera kontroli źródła (składnik programu Visual Studio, który obsługuje funkcje kontroli źródła za pośrednictwem wtyczek kontroli źródła)

   W odpowiedzi na polecenie kontroli źródła środowisko IDE programu Visual Studio prezentuje standardowy interfejs użytkownika dla podstawowych operacji, a następnie przekazuje informacje do wtyczki kontroli źródła za pomocą funkcji zdefiniowanych w interfejsie API dodatku plug-in kontroli źródła. W przypadku opcji zaawansowanych wtyczka do kontroli źródła może być wywoływana w celu zaprezentowania własnego interfejsu użytkownika, na przykład w celu przejrzenia projektu z kontrolą źródła. Oznacza to, że użytkownik może być prezentowany z dwoma prawdopodobnie różnymi stylami interfejsu użytkownika podczas pracy z kontrolą źródła: interfejs użytkownika, który prezentuje program Visual Studio i interfejs użytkownika, który prezentuje wtyczka do kontroli źródła. Jest to najbardziej zauważalne w przypadku zaawansowanych operacji kontroli źródła.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Wady dotyczące implementacji wtyczki kontroli źródła

- W przypadku zaawansowanych funkcji użytkownik może zobaczyć dwa różne style interfejsów, co prowadzi do ewentualnych pomyłek.

- Wtyczka kontroli źródła jest ograniczona do modelu kontroli źródła implikowanego przez interfejs API wtyczki kontroli źródła.

- Interfejs API wtyczki kontroli źródła może być zbyt restrykcyjny w niektórych scenariuszach kontroli źródła.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Zalety wdrożenia wtyczki kontroli źródła

- Program Visual Studio udostępnia wszystkie podstawowe operacje kontroli źródła, dzięki czemu wtyczka do kontroli źródła nie musi implementować potencjalnie złożonego interfejsu użytkownika.

- Ze względu na ścisły interfejs API wtyczka do kontroli źródła może łatwo współdziałać z zewnętrznymi programami kontroli źródła, aby zapewnić bardziej rozległą funkcjonalność. Program Visual Studio nie chroni zbyt dużej liczby funkcji kontroli źródła, tylko że jest realizowany zgodnie z interfejsem API kontroli źródła.

- Łatwiej jest zaimplementować wtyczkę kontroli źródła niż pakietu VSPackage kontroli źródła.

## <a name="source-control-vspackage"></a>Pakietu VSPackage kontroli źródła
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] umożliwia głębokiej integracji z programem Visual Studio i pełną kontrolę nad funkcjami kontroli źródła i pełną wymianą interfejsu użytkownika kontroli źródła programu Visual Studio. Pakietu VSPackage kontroli źródła jest zarejestrowany w programie Visual Studio i udostępnia funkcje kontroli źródła. Chociaż kilka pakietów VSPackage kontroli źródła można zarejestrować w programie Visual Studio, tylko jeden z nich może być aktywny w dowolnym czasie. Pakietu VSPackage kontroli źródła ma pełną kontrolę nad funkcjami kontroli źródła i wyglądem w programie Visual Studio, gdy jest aktywny. Wszystkie inne pakietów VSPackage kontroli źródła, które mogą być zarejestrowane w systemie, są nieaktywne i nie będą wyświetlać żadnego interfejsu użytkownika.

 Implementacja kontroli źródła pakietu VSPackage wymaga strategii "all or Nothing". Twórca kontroli źródła pakietu VSPackage musi zainwestować znaczną ilość wysiłku w celu zaimplementowania wielu interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okien dialogowych, menu i pasków narzędzi) w celu pokrycia całej funkcjonalności kontroli źródła. Aby uzyskać więcej informacji [, zobacz Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md) .

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Wady dotyczące implementacji pakietu VSPackage kontroli źródła

- Pakietu VSPackage musi implementować szereg złożonych interfejsów do pomyślnego zintegrowania z programem Visual Studio.

- Pakietu VSPackage musi dostarczyć wszystkie elementy interfejsu użytkownika wymagane do kontroli źródła; Program Visual Studio nie zapewnia pomocy w tym obszarze.

- Pakietu VSPackage kontroli źródła jest dokładnie powiązane z programem Visual Studio i nie może działać w przypadku programów autonomicznych, dlatego funkcje nie mogą być łatwo udostępniane z zewnętrzną wersją programu kontroli źródła.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Zalety do wdrożenia pakietu VSPackage kontroli źródła

- Ponieważ pakietu VSPackage ma pełną kontrolę nad interfejsem użytkownika i funkcjonalnością kontroli źródła, użytkownik jest prezentowany z bezproblemowym interfejsem kontroli źródła.

- Pakietu VSPackage nie jest ograniczone do określonego modelu kontroli źródła.

## <a name="see-also"></a>Zobacz też
- [Kontrola źródła](../../extensibility/internals/source-control.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Nowości dotyczące kontroli kodu źródłowego](../../extensibility/internals/what-s-new-in-source-control.md)
