---
title: Udostępnianie zdarzeń w sdk programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708489"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Udostępnianie zdarzeń w sdk programu Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]umożliwia pozyskiwanie zdarzeń przy użyciu automatyzacji. Zaleca się, aby źródła zdarzeń dla projektów i elementów projektu.

 Zdarzenia są pobierane przez konsumentów <xref:EnvDTE.DTEClass.Events%2A> automatyzacji z obiektu lub <xref:EnvDTE.DTEClass.GetObject%2A> (na przykład `GetObject("EventObjectName")`). Środowisko wywołuje `IDispatch::Invoke` za `DISPATCH_METHOD` pomocą `DISPATCH_PROPERTYGET` lub flagi, aby zwrócić zdarzenie.

 Poniższy proces wyjaśnia, jak vspackage zdarzenia specyficzne są zwracane.

1. Środowisko się uruchamia.

2. Odczytuje z rejestru wszystkie nazwy wartości w obszarze **Automatyzacja**, **AutomationEvents**i **AutomationProperties** klucze wszystkich VSPackages i przechowuje te nazwy w tabeli.

3. Wywołania konsumenta automatyzacji, `DTE.Events.AutomationProjectsEvents` `DTE.Events.AutomationProjectItemsEvents`w tym przykładzie lub .

4. Środowisko znajduje parametr string w tabeli i ładuje odpowiednie VSPackage.

5. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodę przy użyciu nazwy przekazanej w wywołaniu; w tym `AutomationProjectsEvents` przykładzie lub `AutomationProjectItemsEvents`.

6. VSPackage tworzy obiekt główny, który `get_AutomationProjectsEvents` ma `get_AutomationProjectItemEvents` metody, takie jak, a następnie zwraca wskaźnik IDispatch do obiektu.

7. Środowisko wywołuje odpowiednią metodę na podstawie nazwy przekazywane do wywołania automatyzacji.

8. Metoda `get_` tworzy inny obiekt zdarzenia oparty na IDispatch, który implementuje zarówno `IConnectionPointContainer` interfejs, jak i `IConnectionPoint` interfejs i zwraca `IDispatchpointer` obiekt.

   Aby udostępnić zdarzenie przy użyciu automatyzacji, należy odpowiedzieć <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> i obserwować ciągi, które można dodać do rejestru. W przykładzie Projektu podstawowego ciągi są *BscProjectsEvents* i *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Wpisy rejestru z przykładowego projektu podstawowego
 W tej sekcji pokazano, gdzie należy dodać wartości zdarzeń automatyzacji do rejestru.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = `AutomationProjectEvents` Zwraca obiekt.

 **AutomationProjectItemEvents** = `AutomationProjectItemsEvents` Zwraca obiekt.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|Domyślnie (@)|REG_SZ|Nieużywane|Nieużywany. Można użyć pola danych do dokumentacji.|
|*AutomatyzacjaProjectsWydarzenia*|REG_SZ|Nazwa obiektu zdarzenia.|Tylko nazwa klucza jest istotna. Można użyć pola danych do dokumentacji.<br /><br /> W tym przykładzie pochodzi z przykładu projektu podstawowego.|
|*AutomationProjectItemEvents*|REG_SZ|Nazwa obiektu zdarzenia|Tylko nazwa klucza jest istotna. Można użyć pola danych do dokumentacji.<br /><br /> W tym przykładzie pochodzi z przykładu projektu podstawowego.|

 Gdy którykolwiek z obiektów zdarzenia są wymagane przez konsumenta automatyzacji, należy utworzyć obiekt główny, który ma metody dla dowolnego zdarzenia, które obsługuje VSPackage. Środowisko wywołuje odpowiednią `get_` metodę na tym obiekcie. Na przykład `DTE.Events.AutomationProjectsEvents` jeśli jest `get_AutomationProjectsEvents` wywoływana, metoda na obiekcie głównym jest wywoływana.

 ![Zdarzenia projektu programu Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Model automatyzacji zdarzeń

 Klasa `CProjectEventsContainer` reprezentuje obiekt źródłowy dla *BscProjectsEvents*i `CProjectItemsEventsContainer` reprezentuje obiekt źródłowy dla *BscProjectItemsEvents*.

 W większości przypadków należy zwrócić nowy obiekt dla każdego żądania zdarzenia, ponieważ większość obiektów zdarzeń wziąć obiekt filtru. Po uruchomieniu zdarzenia, sprawdź ten filtr, aby sprawdzić, czy program obsługi zdarzeń jest wywoływany.

 *AutomationEvents.h* i *AutomationEvents.cpp* zawierają deklaracje i implementacje klas w poniższej tabeli.

|Klasa|Opis|
|-----------|-----------------|
|`CAutomationEvents`|Implementuje obiekt główny zdarzenia, pobrany z `DTE.Events` obiektu.|
|`CProjectsEventsContainer` i `CProjectItemsEventsContainer`|Zaimplementuj obiekty źródłowe zdarzeń, które uruchamiają odpowiednie zdarzenia.|

 Poniższy przykład kodu pokazuje, jak odpowiedzieć na żądanie dla obiektu zdarzenia.

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

 W powyższym `g_wszAutomationProjects` kodzie jest nazwa kolekcji projektu ( `g_wszAutomationProjectsEvents` *FigProjects*), (*FigProjectsEvents*) i `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) są nazwy zdarzeń projektu i elementów projektu zdarzenia, które pochodzą z implementacji VSPackage.

 Obiekty zdarzeń są pobierane z tej `DTE.Events` samej centralnej lokalizacji, obiektu. W ten sposób wszystkie obiekty zdarzeń są zgrupowane razem, dzięki czemu użytkownik końcowy nie musi przeglądać całego modelu obiektu, aby znaleźć określone zdarzenie. Dzięki temu można również podać konkretne obiekty VSPackage, zamiast wymagać zaimplementowania własnego kodu dla zdarzeń całego systemu. Jednak dla użytkownika końcowego, który musi `ProjectItem` znaleźć zdarzenie dla interfejsu, nie jest natychmiast jasne, gdzie ten obiekt zdarzenia jest pobierany.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
