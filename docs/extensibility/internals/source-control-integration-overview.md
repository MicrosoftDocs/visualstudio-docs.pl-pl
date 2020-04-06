---
title: Omówienie integracji kontroli źródła | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705124"
---
# <a name="source-control-integration-overview"></a>Omówienie integracji kontroli kodu źródłowego
W tej sekcji porównuje dwa sposoby integracji z formantu źródła programu Visual Studio; wtyczka kontroli źródła i VSPackage, który zapewnia rozwiązanie kontroli źródła i wyróżnia nowe funkcje kontroli źródła. Visual Studio umożliwia ręczne przełączanie między vspackages kontroli źródła i wtyczki kontroli źródła, a także automatyczne przełączanie oparte na rozwiązaniach.

## <a name="source-control-integration"></a>Integracja kontroli źródła
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje dwa typy opcji integracji kontroli źródła. We wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wersjach programu , nadal można zintegrować wtyczkę opartą na interfejsie API wtyczki kontroli źródła (wcześniej nazywanym również interfejsem API MSSCCI), który zapewnia podstawową funkcję kontroli źródła podczas korzystania z interfejsu użytkownika kontroli źródła programu Visual Studio (UI). VsPackage kontroli źródła, z drugiej strony, zapewnia nową [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ścieżkę głębokiej integracji nadaje się do integracji kontroli źródła, który wymaga wysokiego poziomu wyrafinowania i autonomii w swoim modelu kontroli źródła.

 ![Omówienie kontroli źródła](../../extensibility/internals/media/sourcectnrloverview.gif "Widok źródłowyCtnrlOverview")

## <a name="source-control-plug-in"></a>Wtyczka kontroli źródła
 Wszystkie wersje programu Visual Studio obsługują specyfikację interfejsu API dodatku 1.2 wtyczki kontroli źródła jako ścieżkę integracji. Implementator dodatku plug-in kontroli źródła zapisuje bibliotekę DLL, która implementuje funkcje interfejsu API dodatku Plug-in for source w celu integracji i rejestracji kontroli źródła, jak opisano w [temacie Tworzenie wtyczki kontroli źródła.](../../extensibility/internals/creating-a-source-control-plug-in.md) W tym podejściu zintegrowane środowisko programistyczne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) używa interfejsu użytkownika dla okien dialogowych, takich jak ewidencjonowanie, wyewidencjonowanie, strony właściwości narzędzia/opcje, paski narzędzi i glify kontroli źródła. Ścisłe przestrzeganie interfejsu API wtyczki kontroli źródła zapewnia łatwą integrację z programem Visual Studio i bezproblemowe środowisko dla użytkownika. Oznacza to, że wtyczka kontroli źródła musi implementować większość funkcji i wywołań zwrotnych wgłębnych w interfejsie API.

 Aby zaimplementować wtyczkę kontroli źródła przy użyciu interfejsu API dodatku Plug-in wtyczki kontroli źródła, wykonaj następujące kroki:

1. Utwórz bibliotekę DLL, która implementuje funkcje określone w [wtyczkach kontroli źródła](../../extensibility/source-control-plug-ins.md).

2. Zarejestruj bibliotekę DLL, dokonując odpowiednich wpisów rejestru (opisanych w [: Jak: Zainstaluj wtyczkę kontroli źródła).](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Tworzenie pomocniczego interfejsu użytkownika i wyświetlanie po wyświetleniu monitu przez pakiet karty kontroli źródła (składnik visual studio, który obsługuje funkcje kontroli źródła za pośrednictwem wtyczek kontroli źródła)

   W odpowiedzi na polecenie kontroli źródła ide programu Visual Studio przedstawia standardowy interfejs użytkownika dla podstawowych operacji, a następnie przekazuje informacje do wtyczki kontroli źródła za pośrednictwem funkcji zdefiniowanych w interfejsie API wtyczki kontroli źródła. W przypadku zaawansowanych opcji można wywołać wtyczkę kontroli źródła w celu przedstawienia własnego interfejsu użytkownika, na przykład przeglądania projektu kontrolowanego przez źródło. Oznacza to, że użytkownik może być przedstawiony z dwóch ewentualnie różnych stylów interfejsu użytkownika w kontaktach z kontrolą źródła: interfejsu użytkownika, który visual studio prezentuje i interfejsu użytkownika, który prezentuje wtyczki kontroli źródła. Jest to najbardziej zauważalne w przypadku zaawansowanych operacji kontroli źródła.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Wady implementacji wtyczki kontroli źródła

- W przypadku zaawansowanych funkcji użytkownik może zobaczyć dwa różne style interfejsów, co prowadzi do ewentualnego zamieszania.

- Wtyczka kontroli źródła jest ograniczona do modelu kontroli źródła implikowane przez interfejs API wtyczki kontroli źródła.

- Interfejs API wtyczki kontroli źródła może być zbyt restrykcyjne dla niektórych scenariuszy kontroli źródła.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Zalety wdrażania wtyczki kontroli źródła

- Visual Studio dostarcza wszystkie interfejsu użytkownika dla wszystkich podstawowych operacji kontroli źródła, dzięki czemu wtyczka kontroli źródła nie musi implementować potencjalnie złożony interfejs użytkownika.

- Ze względu na ścisły interfejs API wtyczka kontroli źródła może łatwo wchodzić w interakcje z zewnętrznymi programami kontroli źródła, aby zapewnić bardziej rozbudowaną funkcjonalność; Visual Studio nie obchodzi zbyt wiele, jak funkcja kontroli źródła jest spełniony, tylko, że jest ono realizowane zgodnie z interfejsem API wtyczki kontroli źródła.

- Łatwiej jest zaimplementować wtyczkę kontroli źródła niż formantu źródłowego VSPackage.

## <a name="source-control-vspackage"></a>Kontrola źródła VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]umożliwia głęboką integrację z programem Visual Studio z pełną kontrolą funkcji kontroli źródła i pełne zastąpienie interfejsu użytkownika kontroli źródła dostarczonych przez program Visual Studio. Formant źródła VSPackage jest zarejestrowany w programie Visual Studio i zapewnia funkcje kontroli źródła. Chociaż kilka kontroli źródła VSPackages mogą być zarejestrowane w programie Visual Studio, tylko jeden z nich może być aktywny w dowolnym momencie. Formant źródłowy VSPackage ma pełną kontrolę nad funkcją kontroli źródła i wygląd w programie Visual Studio, gdy jest aktywny. Wszystkie inne formanty źródła VSPackages, które mogą być zarejestrowane w systemie są nieaktywne i nie będzie wyświetlany żaden interfejs użytkownika w ogóle.

 Implementowanie kontroli źródła VSPackage wymaga strategii "wszystko albo nic". Twórca kontroli źródła VSPackage musi zainwestować znaczną ilość wysiłku w implementację wielu interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okna dialogowe, menu i paski narzędzi) w celu pokrycia całej funkcji kontroli źródła. Zobacz [Tworzenie formantu źródła VSPackage aby](../../extensibility/internals/creating-a-source-control-vspackage.md) uzyskać więcej informacji.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Wady implementacji vspackage kontroli źródła

- VSPackage należy zaimplementować szereg złożonych interfejsów, aby pomyślnie zintegrować z programem Visual Studio.

- VSPackage musi dostarczyć wszystkie interfejsu użytkownika wymagane do kontroli źródła; Visual Studio nie zapewni żadnej pomocy w tym obszarze.

- Formant źródłowy VSPackage jest ściśle związany z programem Visual Studio i nie może działać z autonomicznymi programami, więc funkcjonalność nie może być tak łatwo współużytkowana z zewnętrzną wersją programu kontroli źródła.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Zalety implementacji vspackage kontroli źródła

- Ponieważ VSPackage ma pełną kontrolę nad interfejsem użytkownika kontroli źródła i funkcji, użytkownik jest przedstawiony z interfejsem bezproblemowe dla kontroli źródła.

- VSPackage nie ogranicza się do określonego modelu kontroli źródła.

## <a name="see-also"></a>Zobacz też
- [Kontrola źródła](../../extensibility/internals/source-control.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Nowości dotyczące kontroli kodu źródłowego](../../extensibility/internals/what-s-new-in-source-control.md)
