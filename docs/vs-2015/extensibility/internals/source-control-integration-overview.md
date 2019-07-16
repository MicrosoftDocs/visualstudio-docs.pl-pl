---
title: Omówienie integracji kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e2761958cd60721ccf05a14ec54d3e365572ea1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148377"
---
# <a name="source-control-integration-overview"></a>Omówienie integracji kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tej sekcji porównuje dwa sposoby integracji kontroli źródła programu Visual Studio; kontroli źródła wtyczek i pakietu VSPackage, który zapewnia rozwiązanie do kontroli źródła i wyróżnienie nowej funkcji kontroli źródła. Program Visual Studio umożliwia ręczne przełączanie między kontroli źródła pakietów VSPackage i wtyczek kontroli kodu źródłowego, a także automatyczne przełączanie oparte na rozwiązaniach.  
  
## <a name="source-control-integration"></a>Integracja kontroli źródła  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje dwa typy opcji integracji kontroli źródła. We wszystkich wersjach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], nadal można zintegrować wtyczki na podstawie źródła kontroli wtyczki interfejsu API (wcześniej również nazywane MSSCCI interfejsu API), która zapewnia funkcjonalność formantu podstawowego źródła podczas korzystania z programu Visual Studio źródła kontrolki użytkownika interfejsu ( INTERFEJS UŻYTKOWNIKA). Kontroli źródła pakietu VSPackage, z drugiej strony, oferuje nowy, integracja głębokiego [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ścieżki umożliwiających integrację kontroli źródła, który wymaga wysokiego poziomu zaawansowania i autonomię w jego model kontroli źródła.  
  
 ![Informacje o formancie źródła](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Wtyczka do kontroli źródła  
 Wszystkie wersje programu Visual Studio obsługuje API wtyczki kontroli źródła specyfikacji wersji 1.2, jako ścieżkę integracji. Implementujący wtyczki kontroli źródła zapisuje biblioteki DLL, która implementuje funkcje interfejsu API wtyczki kontroli źródła, Integracja kontroli źródła i rejestracji, zgodnie z opisem w [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md). W tym podejściu używa zintegrowanego środowiska programowania (IDE) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika dla okien dialogowych, takich jak zaewidencjonowania, wyewidencjonowania, strony właściwości narzędzia/Opcje, paski narzędzi i symbole kontroli źródła. Ścisłego przestrzegania API wtyczki kontroli źródła ubezpieczycielom Łatwa integracja w programie Visual Studio i bezproblemowe środowisko użytkownika. Oznacza to, że wtyczka do kontroli źródła musi implementować większość funkcji i wywołania zwrotne w interfejsie API.  
  
 Aby zaimplementować wtyczka do kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, wykonaj następujące kroki:  
  
1. Tworzenie biblioteki DLL, która implementuje funkcje wymienione w [wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md).  
  
2. Zarejestruj plik DLL, wprowadzając wpisy rejestru odpowiednich (opisanego w [jak: Instalowanie wtyczki kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. Utwórz obiekt pomocnika interfejsu użytkownika i wyświetlanie po wyświetleniu monitu przez pakiet karty kontroli źródła (składnik programu Visual Studio, który obsługuje funkcji kontroli źródła, za pomocą wtyczek kontroli kodu źródłowego)  
  
   W odpowiedzi na polecenia kontroli źródła środowiska IDE programu Visual Studio przedstawia standardowego interfejsu użytkownika dla podstawowych operacji, a następnie przekazuje informacje do kontroli źródła wtyczek przy użyciu funkcje zdefiniowane w interfejsie API wtyczki kontroli źródła. Zaawansowane opcje wtyczka do kontroli źródła może być wywołana dla aby zaprezentować swój własny interfejs użytkownika, na przykład przeglądanie dla projektu z kontrolą źródła. Oznacza to, czy użytkownik może pojawić się dwa prawdopodobnie różne style interfejsu użytkownika podczas pracy z kontrolą źródła: interfejs użytkownika, który przedstawia informacje o programie Visual Studio i interfejs użytkownika, który przedstawia wtyczka do kontroli źródła. Jest to najbardziej zauważalne w przypadku operacji kontroli źródła zaawansowane.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Wady do wdrażania wtyczki kontroli źródła  
  
- Zaawansowane funkcje użytkownik może uzyskać dwa różne style interfejsów, prowadzące do potencjalne problemy.  
  
- Wtyczka do kontroli źródła jest ograniczona do model kontroli źródła, dorozumianych przez interfejs API wtyczki kontroli źródła.  
  
- Interfejs API wtyczki kontroli źródła może być zbyt restrykcyjna dla niektórych scenariuszy kontroli źródła.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Zalety do wdrażania wtyczki kontroli źródła  
  
- Program Visual Studio dostarcza wszystkich w interfejsie użytkownika dla wszystkich operacji kontroli źródła podstawowe tak, aby wtyczka do kontroli źródła nie trzeba implementować złożonych interfejsu użytkownika.  
  
- Ze względu na ścisłym interfejsu API wtyczka do kontroli źródła można łatwo interakcję z programami kontroli zewnętrznego źródła, aby zapewnić bardziej rozległe funkcjonalności. Program Visual Studio nie się zbyt dużo jak funkcji kontroli źródła jest realizowane, tylko że odbywa się zgodnie z interfejsu API wtyczki kontroli źródła.  
  
- Jest to łatwiejsze do wdrożenia wtyczka do kontroli źródła niż pakietu VSPackage kontroli źródła.  
  
## <a name="source-control-vspackage"></a>Pakiet VSPackage kontroli  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Umożliwia ścisłą integrację do programu Visual Studio z pełną kontrolę nad funkcji kontroli źródła i całkowite zastąpienie interfejsu użytkownika kontroli źródła dostarczone do programu Visual Studio. Pakietu VSPackage kontroli źródła jest zarejestrowany w programie Visual Studio i zapewnia funkcji kontroli źródła. Chociaż kilka kontroli źródła pakietów VSPackage można zarejestrować za pomocą programu Visual Studio, tylko jeden z nich może być aktywny w dowolnym momencie. Kontroli źródła pakietu VSPackage ma pełną kontrolę nad funkcji kontroli źródła i wyglądu w programie Visual Studio, gdy jest aktywny. Wszystkie inne kontroli źródła pakietów VSPackage, który może zostać zarejestrowana w systemie nie są aktywne i nie będą wyświetlane wszelkich elementów interfejsu użytkownika na wszystkich.  
  
 Implementowanie kontroli źródła pakietu VSPackage wymaga strategii "wszystko lub nic". Twórca pakietu VSPackage kontroli źródła należy zakupić znacznej ilości wysiłku we wdrażaniu pewną liczbę interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okna dialogowe, menu i pasków narzędzi) obejmują funkcji kontroli źródła całego. Zobacz [tworzenia VSPackage kontroli kodu](../../extensibility/internals/creating-a-source-control-vspackage.md) Aby uzyskać więcej informacji.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Wady do wdrażania pakietu VSPackage kontroli źródła  
  
- Pakietu VSPackage musi implementować liczby złożone interfejsy pomyślnie integracji z programem Visual Studio.  
  
- Pakietu VSPackage należy podać wszystkie wymagane do kontroli źródła; interfejsu użytkownika Program Visual Studio zapewnia nie pomocy, w tym obszarze.  
  
- Pakietu VSPackage kontroli źródła jest ściśle powiązany z programu Visual Studio i nie może działać przy użyciu programów autonomicznych, dzięki funkcji nie można łatwo udostępniać zewnętrznych wersji programu kontroli źródła.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Zalety do wdrażania pakietu VSPackage kontroli źródła  
  
- Ponieważ pakietu VSPackage ma pełną kontrolę nad interfejsu użytkownika do kontroli źródła i funkcji, użytkownik zostanie wyświetlony interfejs do kontroli źródła.  
  
- Pakietu VSPackage nie jest ograniczona do modelu kontroli określonego źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola źródła](../../extensibility/internals/source-control.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Nowości dotyczące kontroli kodu źródłowego](../../extensibility/internals/what-s-new-in-source-control.md)
