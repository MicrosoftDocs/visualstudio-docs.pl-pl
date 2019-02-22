---
title: Udostępnianie zdarzeń w programie Visual Studio SDK | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cc905e359d7bcb2946d627ebcb3c28067233fa0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603160"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Udostępnianie zdarzeń w Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umożliwia źródeł zdarzeń za pomocą automatyzacji. Zaleca się, że źródła zdarzeń dla projektów i elementów projektu.

 Zderzenia są pobierane przez klientów automatyzacji z <xref:EnvDTE.DTEClass.Events%2A> obiektu lub <xref:EnvDTE.DTEClass.GetObject%2A> (na przykład `GetObject("EventObjectName")`). Wywołania środowiska `IDispatch::Invoke` przy użyciu `DISPATCH_METHOD` lub `DISPATCH_PROPERTYGET` flagi, aby zwrócić zdarzenie.

 Następujący proces wyjaśnia, jak są zwracane zdarzeń specyficznych dla pakietu VSPackage.

1. Uruchamia środowisko.

2. Odczytuje z rejestru wszystkie nazwy wartości w obszarze **automatyzacji**, **AutomationEvents**, i **AutomationProperties** klucze wszystkich pakietów VSPackage i magazyny te nazwy w Tabela.

3. Wywołuje konsumenta automatyzacji, w tym przykładzie `DTE.Events.AutomationProjectsEvents` lub `DTE.Events.AutomationProjectItemsEvents`.

4. Środowisko znajduje parametr ciągu w tabeli i ładuje odpowiedniego pakietu VSPackage.

5. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody przy użyciu nazwy przekazywane w wywołaniu; w tym przykładzie `AutomationProjectsEvents` lub `AutomationProjectItemsEvents`.

6. Pakietu VSPackage tworzy obiekt główny, który zawiera metody, takie jak `get_AutomationProjectsEvents` i `get_AutomationProjectItemEvents` , a następnie zwraca wskaźnik interfejsu IDispatch do obiektu.

7. Środowisko wywołuje odpowiednią metodę na podstawie nazwy przekazane do wywołania usługi automation.

8. `get_` Metoda tworzy inny obiekt zdarzeń w oparciu o IDispatch, który implementuje interfejsy `IConnectionPointContainer` interfejsu i `IConnectionPoint` interfejsu i zwraca `IDispatchpointer` do obiektu.

   Aby udostępnić zdarzenia przy użyciu usługi automation, musi odpowiadać na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> i obserwowanie ciągów, które można dodać do rejestru. W tym przykładzie podstawowego projektu ciągi są *BscProjectsEvents* i *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Wpisy rejestru z przykładowym projekcie podstawowe
 W tej sekcji pokazano, gdzie należy dodać wartości zdarzeń automatyzacji do rejestru.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = zwraca `AutomationProjectEvents` obiektu.

 **AutomationProjectItemEvents** = zwraca `AutomationProjectItemsEvents` obiektu.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|Domyślne (@)|REG_SZ|Nieużywane|Nieużywane. Dokumentacja, można użyć pola danych.|
|*AutomationProjectsEvents*|REG_SZ|Nazwa obiektu zdarzenia.|Dotyczy tylko nazwę klucza. Dokumentacja, można użyć pola danych.<br /><br /> W tym przykładzie pochodzi z przykładowym projekcie podstawowe.|
|*AutomationProjectItemEvents*|REG_SZ|Nazwa obiektu zdarzenia|Dotyczy tylko nazwę klucza. Dokumentacja, można użyć pola danych.<br /><br /> W tym przykładzie pochodzi z przykładowym projekcie podstawowe.|

 Gdy dowolne obiekty zdarzeń są wymagane przez konsumenta automatyzacji, należy utworzyć główny obiekt, który posiada metody do dowolnego zdarzenia, który obsługuje Twoja pakietu VSPackage. Środowisko wywołuje odpowiednią `get_` metody dla tego obiektu. Na przykład jeśli `DTE.Events.AutomationProjectsEvents` jest wywoływana, `get_AutomationProjectsEvents` wywołania metody dla obiektu głównego.

 ![Zdarzenia projektu usługi Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") modelu automatyzacji dla zdarzeń

 Klasa `CProjectEventsContainer` reprezentuje obiekt źródłowy dla *BscProjectsEvents*, i `CProjectItemsEventsContainer` reprezentuje obiekt źródłowy dla *BscProjectItemsEvents*.

 W większości przypadków musi zwracać nowy obiekt dla każdego żądania zdarzenia, ponieważ większość obiektów zdarzeń obiektu filtra. Gdy środowisko zdarzenia sprawdza ten filtr, aby sprawdzić, czy program obsługi zdarzeń jest wywoływana.

 *AutomationEvents.h* i *AutomationEvents.cpp* znajdują się deklaracje i implementacje klas w poniższej tabeli.

|Class|Opis|
|-----------|-----------------|
|`CAutomationEvents`|Implementuje obiekt główny zdarzenia pobierane `DTE.Events` obiektu.|
|`CProjectsEventsContainer` i `CProjectItemsEventsContainer`|Implementowanie obiektów źródła zdarzeń, które są aktywowane pokrewnych zdarzeń.|

 W poniższym przykładzie kodu pokazano, jak odpowiedzieć na żądanie dotyczące obiektu zdarzenia.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 W powyższym kodzie `g_wszAutomationProjects` jest nazwą kolekcji projektów (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) i `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents* ) są nazwami zdarzeń związanych z projektem i elementy projektu, zdarzenia, które pochodzą z Twojego wdrożenia pakietu VSPackage.

 Obiekty zdarzeń są pobierane z tej samej lokalizacji centralnej `DTE.Events` obiektu. Dzięki temu wszystkie obiekty zdarzeń są grupowane, aby użytkownik końcowy nie ma do przeglądania modelu całego obiektu, aby znaleźć konkretne wydarzenie. Umożliwia to również podać konkretne obiekty pakietu VSPackage, zamiast konieczności wykonania kodu dla zdarzeń dotyczących całego systemu. Jednak dla użytkownika końcowego, który należy znaleźć zdarzenie dla Twojego `ProjectItem` interfejsu nie jest od razu jasne, z której ten obiekt jest pobierany.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
