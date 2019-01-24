---
title: Przewodnik wtyczek kontroli kodu źródłowego testowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194c1e926ead79d5db05e530e2345aa4c722aa21
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776443"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Przewodnik testowania wtyczek kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta sekcja zawiera wskazówki dotyczące testowania Twojego wtyczka do kontroli źródła przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Rozbudowane przegląd typowych obszarów, testowania, a także niektórych bardziej skomplikowanych obszarów, które może być problematyczne, jest dostępna. W tym omówieniu nie stanowi wyczerpującej listy przypadków testowych.  
  
> [!NOTE]
>  Kilka poprawek usterek i usprawnień do najnowszej wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE może wykryć problemy z istniejącego źródła wtyczek kontroli napotkanych wcześniej nie podczas korzystania z poprzednich wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Zdecydowanie zaleca się, testowanie istniejących wtyczka do kontroli źródła dla obszarów, wymienione w tej sekcji, nawet jeśli żadne zmiany nie zostały wprowadzone do wtyczki od poprzedniej wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="common-preparation"></a>Typowe przygotowania  
 Maszyna z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i wtyczki kontroli źródła docelowej zainstalowany, jest wymagany. Druga maszyna podobnie skonfigurowane może służyć do niektórych otwierania z kontroli źródła testów.  
  
## <a name="definition-of-terms"></a>Definicje terminów  
 Na potrzeby tego przewodnika testów należy użyć następujące definicje terminów:  
  
 Projekt klienta  
 Każdy projekt typu dostępne w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , która obsługuje integrację kontroli źródła (na przykład [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], lub [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]).  
  
 Projekt sieci Web  
 Istnieją cztery rodzaje projektów sieci Web: System plików, lokalnych usług IIS, lokacjami zdalnymi i FTP.  
  
- Projekty systemu plików są tworzone na ścieżkę lokalną, ale nie wymagają Internet Information Services (IIS) do zainstalowania, ponieważ są używane wewnętrznie za pośrednictwem ścieżki UNC i można umieścić pod kontrolą źródła z wewnątrz IDE, podobnie jak projektów klienckich.  
  
- Lokalnych projektów usług IIS działają z usługami IIS zainstalowane na tym samym komputerze, które są dostępne przy użyciu adresu URL, wskazując na komputerze lokalnym.  
  
- Zdalne projektów witryny są również tworzone w ramach usług IIS, ale są one umieszczone pod kontrolą źródła, na komputerze serwera usług IIS, a nie z wewnątrz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
- Projekty FTP są dostępne za pośrednictwem zdalnego serwera FTP, ale nie mogą być umieszczone pod kontrolą źródła.  
  
  Funkcja rejestracji  
  Inna nazwa rozwiązania lub projektu objętego kontrolą źródła.  
  
  Wersja Store  
  Bazy danych kontroli źródła, jest uzyskiwany za pośrednictwem interfejsu API wtyczki kontroli źródła.  
  
## <a name="test-areas-covered-in-this-section"></a>Obszary testów, opisanych w tej sekcji  
  
-   [Obszar testowy 1: Dodaj / Otwórz z kontroli źródła](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Wielkość 1a: Dodaj rozwiązanie do kontroli źródła  
  
    -   Wielkość 1b: Otwórz rozwiązanie z kontroli źródła  
  
    -   Przypadek 1c: Dodaj rozwiązanie z kontroli źródła  
  
-   [Obszar testowy 2: Pobieranie z kontroli źródła](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Obszar testowy 3: Zapoznaj się z / Cofnij wyewidencjonowanie](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Przypadek 3: Zapoznaj się z / Cofnij wyewidencjonowanie  
  
    -   Wielkości liter 3a: Wyewidencjonuj  
  
    -   Wielkość 3b: Wyewidencjonowanie bez połączenia  
  
    -   Przypadek 3c: Edytuj zapytanie/zapytanie Zapisz (QEQS)  
  
    -   Zamierzone, Zapisz 3d: Dyskretnej wyewidencjonowania  
  
    -   Wielkość 3e: Cofnij wyewidencjonowanie  
  
-   [Obszar testowy 4: Zamelduj się](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Wielkość 4a: Zmodyfikowane elementy  
  
    -   Wielkość 4b: Trwa dodawanie plików  
  
    -   W przypadku 4c: Dodawanie projektów  
  
-   [Obszar testowy 5: Zmień kontrolę źródła](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Wielkość 5a: powiązania  
  
    -   Wielkość 5b: Usuń powiązanie  
  
    -   W przypadku 5c: ponowne wiązanie  
  
-   [Obszar testowy 6: Usuń](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Obszar testowy 7: Udostępnij](../../extensibility/internals/test-area-7-share.md)  
  
-   [Obszar testowy 8: Przełączanie wtyczki](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   8a przypadków: Automatyczna zmiana  
  
    -   8b przypadków: Oparte na rozwiązaniach zmiany  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)
