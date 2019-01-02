---
title: Zarządzanie rolami w usługach Azure cloud services
description: Dowiedz się, jak dodawanie i usuwanie ról w usługach Azure cloud services z programem Visual Studio.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 23e780c7de528481d5809e86af67816827f724d8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868607"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Zarządzanie rolami w usługach Azure cloud services z programem Visual Studio
Po utworzeniu usługi w chmurze platformy Azure, możesz dodać nowe role do niego lub usuwać istniejące role. Można także zaimportować istniejący projekt i przekonwertować go do roli. Na przykład można zaimportować aplikację sieci web platformy ASP.NET i określić jako rola sieć web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Dodawanie roli w usłudze w chmurze platformy Azure
Poniższe kroki prowadzą przez proces dodawania roli sieć web lub procesu roboczego do projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, rozwiń węzeł projektu

1. Kliknij prawym przyciskiem myszy **role** węzeł, aby wyświetlić menu kontekstowe. Z menu kontekstowego wybierz **Dodaj**, a następnie wybierz istniejącej roli Internet lub roli procesu roboczego z bieżącego rozwiązania, lub Utwórz projekt roli sieci web lub proces roboczy. Można również wybrać odpowiedni projekt, na przykład projektu aplikacji sieci web programu ASP.NET i skojarzyć go z projektu roli.

    ![Opcje menu, aby dodać rolę do projektu usługi w chmurze platformy Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Usuwanie roli usługi w chmurze platformy Azure
Poniższe kroki prowadzą przez usunięcie roli sieci web lub proces roboczy z projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, rozwiń węzeł projektu

1. Rozwiń **role** węzła.

1. Kliknij prawym przyciskiem myszy węzeł, aby usunąć i z menu kontekstowego wybierz **Usuń**. 

    ![Opcje menu, aby dodać rolę w usłudze w chmurze platformy Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Ponownie dodać roli do projektu usługi w chmurze platformy Azure
Jeśli usunąć rolę z projektu usługi w chmurze, ale później zdecydujesz dodać rolę do projektu, tylko deklaracji ról i podstawowych atrybutów, takich jak punkty końcowe i informacji diagnostycznych, zostaną dodane. Nie dodatkowych zasobów lub odwołania są dodawane do `ServiceDefinition.csdef` pliku lub `ServiceConfiguration.cscfg` pliku. Jeśli chcesz dodać te informacje, należy ręcznie dodać do tych plików.

Na przykład można usunąć roli usługi sieci web, a później zdecydujesz się tę rolę z powrotem dodać do rozwiązania. Jeśli to zrobisz, wystąpi błąd. Aby uniknąć tego błędu, należy dodać `<LocalResources>` elementu objętego następujący kod XML do `ServiceDefinition.csdef` pliku. Użyj nazwy roli usługi sieci web, która zostanie ponownie dodane do projektu jako część atrybut nazwy **<LocalStorage>** elementu. W tym przykładzie nazwa roli usługi sieci web jest **WCFServiceWebRole1**.

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

## <a name="next-steps"></a>Następne kroki
- [Konfigurowanie ról usługi w chmurze platformy Azure przy użyciu programu Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
