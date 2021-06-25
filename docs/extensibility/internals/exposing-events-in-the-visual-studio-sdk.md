---
title: Udostępnianie zdarzeń w zestawie VISUAL STUDIO SDK | Microsoft Docs
description: Dowiedz się więcej Visual Studio zestawu SDK i wpisów rejestru, które uwidoczniają zdarzenia dla projektów i elementów projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99298329b969df3b9d7dbb46a3f4b9e7d4ed7091
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898334"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Uwidocznij zdarzenia w zestawie VISUAL STUDIO SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program umożliwia źródło zdarzeń przy użyciu automatyzacji. Zalecamy używanie zdarzeń źródłowych dla projektów i elementów projektu.

 Zdarzenia są pobierane przez odbiorców automatyzacji z <xref:EnvDTE.DTEClass.Events%2A> obiektu lub <xref:EnvDTE.DTEClass.GetObject%2A> (na przykład `GetObject("EventObjectName")` ). Środowisko wywołuje `IDispatch::Invoke` element przy użyciu `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` flagi lub w celu zwrócenia zdarzenia.

 W poniższym procesie wyjaśniono sposób zwracania zdarzeń specyficznych dla pakietów VSPackage.

1. Środowisko się uruchamia.

2. Odczytuje z rejestru wszystkie nazwy wartości w kluczach **Automation,** **AutomationEvents** i **AutomationProperties** wszystkich pakietów VSPackage i przechowuje te nazwy w tabeli.

3. W tym przykładzie konsument automatyzacji wywołuje `DTE.Events.AutomationProjectsEvents` element lub `DTE.Events.AutomationProjectItemsEvents` .

4. Środowisko znajduje parametr ciągu w tabeli i ładuje odpowiedni pakiet VSPackage.

5. Środowisko wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> przy użyciu nazwy przekazanej w wywołaniu ; w tym przykładzie `AutomationProjectsEvents` jest to metoda lub `AutomationProjectItemsEvents` .

6. Pakiet VSPackage tworzy obiekt główny, który ma metody takie jak i , a następnie zwraca wskaźnik `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` IDispatch do obiektu .

7. Środowisko wywołuje odpowiednią metodę na podstawie nazwy przekazanej do wywołania automatyzacji.

8. Metoda tworzy inny obiekt zdarzenia oparty na interfejsie `get_` IDispatch, który implementuje zarówno interfejs, jak i interfejs i `IConnectionPointContainer` zwraca obiekt do obiektu `IConnectionPoint` `IDispatchpointer` .

   Aby uwidocznić zdarzenie za pomocą automatyzacji, należy odpowiedzieć i obserwować ciągi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> które dodajesz do rejestru. W przykładzie Projektu podstawowego ciągi to *BscProjectsEvents* i *BscProjectItemsEvents.*

## <a name="registry-entries-from-the-basic-project-sample"></a>Wpisy rejestru z przykładu Basic Project
 W tej sekcji pokazano, gdzie dodać wartości zdarzeń automatyzacji do rejestru.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = zwraca `AutomationProjectEvents` obiekt .

 **AutomationProjectItemEvents** = zwraca `AutomationProjectItemsEvents` obiekt .

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|Domyślne (@)|REG_SZ|Nieużywane|Nieużywany. W dokumentacji możesz użyć pola danych.|
|*AutomationProjectsEvents*|REG_SZ|Nazwa obiektu zdarzenia.|Znaczenie ma tylko nazwa klucza. W dokumentacji możesz użyć pola danych.<br /><br /> Ten przykład pochodzi z przykładu Projektu podstawowego.|
|*AutomationProjectItemEvents*|REG_SZ|Nazwa obiektu zdarzenia|Znaczenie ma tylko nazwa klucza. W dokumentacji możesz użyć pola danych.<br /><br /> Ten przykład pochodzi z przykładu Projektu podstawowego.|

 Gdy dowolny obiekt zdarzenia jest żądany przez konsumenta automatyzacji, utwórz obiekt główny, który zawiera metody dla dowolnego zdarzenia, które obsługuje pakiet VSPackage. Środowisko wywołuje odpowiednią metodę `get_` dla tego obiektu. Na przykład, jeśli `DTE.Events.AutomationProjectsEvents` jest wywoływana, wywoływana jest metoda `get_AutomationProjectsEvents` w obiekcie głównym.

 ![Visual Studio zdarzeń projektu](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Model automatyzacji dla zdarzeń

 Klasa `CProjectEventsContainer` reprezentuje obiekt źródłowy obiektu *BscProjectsEvents* i reprezentuje obiekt źródłowy `CProjectItemsEventsContainer` obiektu *BscProjectItemsEvents*.

 W większości przypadków należy zwrócić nowy obiekt dla każdego żądania zdarzenia, ponieważ większość obiektów zdarzeń ma obiekt filtru. Po wywołaniu zdarzenia sprawdź ten filtr, aby sprawdzić, czy program obsługi zdarzeń jest wywoływany.

 *AutomationEvents.h* i *AutomationEvents.cpp* zawierają deklaracje i implementacje klas w poniższej tabeli.

|Klasa|Opis|
|-----------|-----------------|
|`CAutomationEvents`|Implementuje obiekt główny zdarzenia pobrany z `DTE.Events` obiektu .|
|`CProjectsEventsContainer` i `CProjectItemsEventsContainer`|Zaimponuj obiekty źródła zdarzeń, które będą realizować odpowiednie zdarzenia.|

 Poniższy przykład kodu pokazuje, jak odpowiadać na żądanie obiektu zdarzenia.

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

 W powyższym kodzie to nazwa kolekcji projektów `g_wszAutomationProjects` *(FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) i `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) to nazwy zdarzeń projektu i zdarzeń elementów projektu, które pochodzą z implementacji pakietów VSPackage.

 Obiekty zdarzeń są pobierane z tej samej lokalizacji centralnej, obiektu `DTE.Events` . Dzięki temu wszystkie obiekty zdarzeń są grupowane razem, dzięki czemu użytkownik końcowy nie musi przeglądać całego modelu obiektów w celu znalezienia określonego zdarzenia. Dzięki temu można również udostępnić określone obiekty VSPackage, zamiast wymagać implementacji własnego kodu dla zdarzeń dla całego systemu. Jednak w przypadku użytkownika końcowego, który musi znaleźć zdarzenie dla interfejsu, nie jest od razu jasne, skąd ten obiekt `ProjectItem` zdarzenia jest pobierany.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
