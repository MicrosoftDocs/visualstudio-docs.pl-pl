---
title: Zarządzanie rolami w usługach Azure Cloud Services
description: Dowiedz się, jak dodawać i usuwać role w usługach Azure Cloud Services za pomocą programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 897cb36ee2afa650e042b92243c6044684468a6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398842"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Zarządzanie rolami w usługach Azure Cloud Services za pomocą programu Visual Studio
Po utworzeniu usługi w chmurze platformy Azure Możesz dodać do niej nowe role lub usunąć z niej istniejące role. Można także zaimportować istniejący projekt i przekonwertować go do roli. Na przykład możesz zaimportować aplikację sieci Web ASP.NET i wyznaczyć ją jako rolę sieci Web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Dodawanie roli do usługi w chmurze platformy Azure
Poniższe kroki przeprowadzą Cię przez proces dodawania roli sieci Web lub procesu roboczego do projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu

1. Kliknij prawym przyciskiem myszy węzeł **role** , aby wyświetlić menu kontekstowe. Z menu kontekstowego wybierz pozycję **Dodaj** , a następnie wybierz istniejącą rolę sieci Web lub rolę procesu roboczego z bieżącego rozwiązania lub Utwórz projekt roli sieć Web lub proces roboczy. Możesz również wybrać odpowiedni projekt, taki jak projekt aplikacji sieci Web ASP.NET, i skojarzyć go z projektem roli.

   ![Opcje menu umożliwiające dodanie roli do projektu usługi w chmurze platformy Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Usuwanie roli z usługi w chmurze platformy Azure
Poniższe kroki przeprowadzą Cię przez proces usuwania roli sieci Web lub procesu roboczego z projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu

1. Rozwiń węzeł **role** .

1. Kliknij prawym przyciskiem myszy węzeł, który chcesz usunąć, a następnie z menu kontekstowego wybierz pozycję **Usuń**.

   ![Opcje menu umożliwiające dodanie roli do usługi w chmurze platformy Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Dodawanie roli do projektu usługi w chmurze platformy Azure
Jeśli usuniesz rolę z projektu usługi w chmurze, ale później zdecydujesz się dodać rolę z powrotem do projektu, dodawane są tylko deklaracje roli i atrybuty podstawowe, takie jak punkty końcowe i informacje diagnostyczne. Żadne dodatkowe zasoby lub odwołania nie są dodawane do `ServiceDefinition.csdef` pliku lub do `ServiceConfiguration.cscfg` pliku. Jeśli chcesz dodać te informacje, musisz ręcznie dodać je ponownie do tych plików.

Na przykład możesz usunąć rolę usługi sieci Web, a później zdecydujesz się dodać tę rolę z powrotem do rozwiązania. Jeśli to zrobisz, wystąpi błąd. Aby uniknąć tego błędu, należy dodać `<LocalResources>` element przedstawiony w poniższym kodzie XML z powrotem do `ServiceDefinition.csdef` pliku. Użyj nazwy roli usługi sieci Web, która została dodana z powrotem do projektu jako część atrybutu nazwy dla **\<LocalStorage>** elementu. W tym przykładzie nazwa roli usługi sieci Web to **WCFServiceWebRole1**.

```xml
<WebRole name="WCFServiceWebRole1">
    <Sites>
      <Site name="Web">
        <Bindings>
          <Binding name="Endpoint1" endpointName="Endpoint1" />
        </Bindings>
      </Site>
    </Sites>
    <Endpoints>
      <InputEndpoint name="Endpoint1" protocol="http" port="80" />
    </Endpoints>
    <Imports>
      <Import moduleName="Diagnostics" />
    </Imports>
    <LocalResources>
      <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
    </LocalResources>
</WebRole>
```

## <a name="next-steps"></a>Następne kroki
- [Konfigurowanie ról dla usługi w chmurze platformy Azure za pomocą programu Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
