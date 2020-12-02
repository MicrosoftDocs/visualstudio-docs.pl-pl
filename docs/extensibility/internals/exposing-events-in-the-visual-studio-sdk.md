---
title: Uwidacznianie zdarzeń w zestawie Visual Studio SDK | Microsoft Docs
description: Dowiedz się więcej o metodach i wpisach rejestru programu Visual Studio SDK, które uwidaczniają zdarzenia dla projektów i elementów projektu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d5eec842f989497fda618482916154aabdcdd406
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480541"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Uwidacznianie zdarzeń w zestawie Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwia źródło zdarzeń przy użyciu automatyzacji. Zalecamy źródło zdarzeń dla projektów i elementów projektu.

 Zdarzenia są pobierane przez użytkowników usługi Automation z <xref:EnvDTE.DTEClass.Events%2A> obiektu lub <xref:EnvDTE.DTEClass.GetObject%2A> (na przykład `GetObject("EventObjectName")` ). Środowisko wywołuje przy `IDispatch::Invoke` użyciu `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` flag lub w celu zwrócenia zdarzenia.

 Poniższy proces wyjaśnia, jak są zwracane zdarzenia specyficzne dla pakietu VSPackage.

1. Środowisko zostanie uruchomione.

2. Odczytuje z rejestru wszystkie nazwy wartości w kluczach **Automation**, **AutomationEvents** i **AutomationProperties** wszystkich pakietów VSPackage i przechowuje te nazwy w tabeli.

3. Wywołania konsumenta usługi Automation, w tym przykładzie `DTE.Events.AutomationProjectsEvents` lub `DTE.Events.AutomationProjectItemsEvents` .

4. Środowisko znajduje parametr ciągu w tabeli i ładuje odpowiednie pakietu VSPackage.

5. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodę przy użyciu nazwy przekazaną w wywołaniu; w tym przykładzie `AutomationProjectsEvents` lub `AutomationProjectItemsEvents` .

6. Pakietu VSPackage tworzy obiekt główny, który ma metody, takie jak `get_AutomationProjectsEvents` i `get_AutomationProjectItemEvents` , a następnie zwraca wskaźnik IDispatch do obiektu.

7. Środowisko wywołuje odpowiednią metodę na podstawie nazwy przekazaną do wywołania automatyzacji.

8. `get_`Metoda tworzy inny obiekt zdarzenia na podstawie IDispatch, który implementuje `IConnectionPointContainer` interfejs i `IConnectionPoint` interfejs i zwraca `IDispatchpointer` obiekt.

   Aby uwidocznić zdarzenie przy użyciu automatyzacji, musisz odpowiedzieć na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> i obejrzeć ciągi dodawane do rejestru. W podstawowym przykładzie projektu ciągi to *BscProjectsEvents* i *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Wpisy rejestru z przykładu podstawowego projektu
 W tej sekcji przedstawiono, gdzie dodać wartości zdarzeń automatyzacji do rejestru.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID \> \AutomationEvents]**

 **AutomationProjectEvents** = zwraca `AutomationProjectEvents` obiekt.

 **AutomationProjectItemEvents** = zwraca `AutomationProjectItemsEvents` obiekt.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|Wartość domyślna (@)|REG_SZ|Nieużywane|Nieużywany. W celu uzyskania dokumentacji można użyć pola dane.|
|*AutomationProjectsEvents*|REG_SZ|Nazwa obiektu zdarzenia.|Istotna jest tylko nazwa klucza. W celu uzyskania dokumentacji można użyć pola dane.<br /><br /> Ten przykład pochodzi z podstawowego przykładu projektu.|
|*AutomationProjectItemEvents*|REG_SZ|Nazwa obiektu zdarzenia|Istotna jest tylko nazwa klucza. W celu uzyskania dokumentacji można użyć pola dane.<br /><br /> Ten przykład pochodzi z podstawowego przykładu projektu.|

 Gdy klient usługi Automation żąda dowolnego obiektu zdarzenia, Utwórz obiekt główny, który ma metody dla każdego zdarzenia obsługiwanego przez pakietu VSPackage. Środowisko wywołuje odpowiednią `get_` metodę dla tego obiektu. Na przykład, jeśli `DTE.Events.AutomationProjectsEvents` jest wywoływana, `get_AutomationProjectsEvents` Metoda na obiekcie głównym jest wywoływana.

 ![Zdarzenia projektu programu Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Model automatyzacji dla zdarzeń

 Klasa `CProjectEventsContainer` reprezentuje obiekt źródłowy dla *BscProjectsEvents* i `CProjectItemsEventsContainer` reprezentuje obiekt źródłowy dla *BscProjectItemsEvents*.

 W większości przypadków należy zwrócić nowy obiekt dla każdego żądania zdarzenia, ponieważ większość obiektów zdarzeń pobiera obiekt Filter. Gdy uruchamiasz zdarzenie, zaznacz ten filtr, aby sprawdzić, czy program obsługi zdarzeń jest wywoływany.

 *AutomationEvents. h* i *AutomationEvents. cpp* zawierają deklaracje i implementacje klas w poniższej tabeli.

|Klasa|Opis|
|-----------|-----------------|
|`CAutomationEvents`|Implementuje obiekt główny zdarzenia pobrany z `DTE.Events` obiektu.|
|`CProjectsEventsContainer` i `CProjectItemsEventsContainer`|Implementowanie obiektów źródłowych zdarzeń, które wyzwalają odpowiednie zdarzenia.|

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

 W powyższym kodzie, `g_wszAutomationProjects` jest nazwą kolekcji projektu (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) i `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents*) są nazwami zdarzeń projektu i zdarzeń elementów projektu, które są źródłem z implementacji pakietu VSPackage.

 Obiekty zdarzeń są pobierane z tej samej centralnej lokalizacji, `DTE.Events` obiektu. Dzięki temu wszystkie obiekty zdarzeń są pogrupowane w taki sposób, aby użytkownicy końcowi nie musieli przeglądać całego modelu obiektów w celu znalezienia konkretnego zdarzenia. Umożliwia to również dostarczenie określonych obiektów pakietu VSPackage, zamiast konieczności implementowania własnego kodu dla zdarzeń na poziomie systemu. Jednak dla użytkownika końcowego, który musi znaleźć zdarzenie dla `ProjectItem` interfejsu, nie jest natychmiast czyszczony od miejsca, w którym jest pobierany obiekt zdarzenia.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
