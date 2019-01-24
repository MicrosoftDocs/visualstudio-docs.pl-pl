---
title: Udostępnianie zdarzeń w programie Visual Studio SDK | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7056497c505bbb355287416e468e411b4e5a2a62
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763720"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Udostępnianie zdarzeń w zestawie Visual Studio SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umożliwia źródeł zdarzeń za pomocą automatyzacji. Zaleca się, że źródła zdarzeń dla projektów i elementów projektu.  
  
 Zderzenia są pobierane przez klientów automatyzacji z <xref:EnvDTE.DTEClass.Events%2A> obiektu lub <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). Wywołania środowiska `IDispatch::Invoke` przy użyciu `DISPATCH_METHOD` lub `DISPATCH_PROPERTYGET` flagi, aby zwrócić zdarzenie.  
  
 Następujący proces wyjaśnia, jak są zwracane zdarzeń specyficznych dla pakietu VSPackage.  
  
1. Uruchamia środowisko.  
  
2. Odczytuje z rejestru wszystkie nazwy wartości w ramach usługi Automation, AutomationEvents i AutomationProperties klucze wszystkich pakietów VSPackage, a te nazwy są przechowywane w tabeli.  
  
3. Wywołuje konsumenta automatyzacji, w tym przykładzie `DTE.Events.AutomationProjectsEvents` lub `DTE.Events.AutomationProjectItemsEvents`.  
  
4. Środowisko znajduje parametr ciągu w tabeli i ładuje odpowiedniego pakietu VSPackage.  
  
5. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody przy użyciu nazwy przekazywane w wywołaniu; w tym przykładzie AutomationProjectsEvents lub AutomationProjectItemsEvents.  
  
6. Pakietu VSPackage tworzy obiekt główny, który zawiera metody, takie jak `get_AutomationProjectsEvents` i `get_AutomationProjectItemEvents` , a następnie zwraca wskaźnik interfejsu IDispatch do obiektu.  
  
7. Środowisko wywołuje odpowiednią metodę na podstawie nazwy przekazane do wywołania usługi automation.  
  
8. `get_` Metoda tworzy inny obiekt zdarzeń w oparciu o IDispatch, który implementuje interfejsy `IConnectionPointContainer` interfejsu i `IConnectionPoint` interfejs i zwraca IDispatchpointer do obiektu.  
  
   Aby udostępnić zdarzenia przy użyciu usługi automation, musi odpowiadać na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> i obserwowanie ciągów, które można dodać do rejestru. W przykładowym projekcie podstawowe ciągi są "BscProjectsEvents" i "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Wpisy rejestru z przykładowym projekcie podstawowe  
 W tej sekcji pokazano, gdzie należy dodać wartości zdarzeń automatyzacji do rejestru.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents"="zwraca obiekt AutomationProjectEvents"  
  
 "AutomationProjectItemEvents"="zwraca obiekt AutomationProjectItemsEvents"  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|Domyślne (@)|REG_SZ|Nieużywane|Nieużywane. Dokumentacja, można użyć pola danych.|  
|AutomationProjectsEvents|REG_SZ|Nazwa obiektu zdarzenia.|Dotyczy tylko nazwę klucza. Dokumentacja, można użyć pola danych.<br /><br /> W tym przykładzie pochodzi z przykładowym projekcie podstawowe.|  
|AutomationProjectItemEvents|REG_SZ|Nazwa obiektu zdarzenia|Dotyczy tylko nazwę klucza. Dokumentacja, można użyć pola danych.<br /><br /> W tym przykładzie pochodzi z przykładowym projekcie podstawowe.|  
  
 Gdy dowolne obiekty zdarzeń są wymagane przez konsumenta automatyzacji, należy utworzyć główny obiekt, który posiada metody do dowolnego zdarzenia, który obsługuje Twoja pakietu VSPackage. Środowisko wywołuje odpowiednią `get_` metody dla tego obiektu. Na przykład jeśli `DTE.Events.AutomationProjectsEvents` jest wywoływana, `get_AutomationProjectsEvents` wywołania metody dla obiektu głównego.  
  
 ![Zdarzenia projektu programu Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Model automatyzacji dla zdarzeń  
  
 Klasa `CProjectEventsContainer` reprezentuje obiekt źródłowy dla BscProjectsEvents, podczas gdy `CProjectItemsEventsContainer` reprezentuje obiekt źródłowy dla BscProjectItemsEvents.  
  
 W większości przypadków musi zwracać nowy obiekt dla każdego żądania zdarzenia, ponieważ większość obiektów zdarzeń obiektu filtra. Gdy środowisko zdarzenia sprawdza ten filtr, aby sprawdzić, czy program obsługi zdarzeń jest wywoływana.  
  
 AutomationEvents.h i AutomationEvents.cpp zawierać deklaracje i implementacje klas w poniższej tabeli.  
  
|Class|Opis|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementuje obiekt główny zdarzenia pobierane `DTE.Events` obiektu.|  
|`CProjectsEventsContainer` i `CProjectItemsEventsContainer`|Implementowanie obiektów źródła zdarzeń, które są aktywowane pokrewnych zdarzeń.|  
  
 W poniższym przykładzie kodu pokazano, jak odpowiedzieć na żądanie dotyczące obiektu zdarzenia.  
  
```cpp#  
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
  
 W powyższym kodzie `g_wszAutomationProjects` jest nazwą kolekcji projektów ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") i `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") są nazwami zdarzeń związanych z projektem i elementy projektu, zdarzenia, które pochodzą z usługi Implementacja pakietu VSPackage.  
  
 Obiekty zdarzeń są pobierane z tej samej lokalizacji centralnej `DTE.Events` obiektu. Dzięki temu wszystkie obiekty zdarzeń są grupowane, aby użytkownik końcowy nie ma do przeglądania modelu całego obiektu, aby znaleźć konkretne wydarzenie. Umożliwia to również podać konkretne obiekty pakietu VSPackage, zamiast konieczności wykonania kodu dla zdarzeń dotyczących całego systemu. Jednak dla użytkownika końcowego, który należy znaleźć zdarzenie dla Twojego `ProjectItem` interfejsu nie jest od razu jasne, z której ten obiekt jest pobierany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Przykłady VSSDK](../../misc/vssdk-samples.md)
