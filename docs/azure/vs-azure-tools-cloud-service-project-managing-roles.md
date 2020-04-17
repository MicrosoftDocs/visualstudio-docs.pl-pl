---
title: Zarządzanie rolami w usługach w chmurze platformy Azure
description: Dowiedz się, jak dodawać i usuwać role w usługach w chmurze platformy Azure za pomocą programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: f03ac134a54f3a32108175fa858d22b5c4aec8af
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489691"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Zarządzanie rolami w usługach w chmurze platformy Azure za pomocą programu Visual Studio
Po utworzeniu usługi w chmurze platformy Azure można dodać do niej nowe role lub usunąć z niej istniejące role. Można również zaimportować istniejący projekt i przekonwertować go na rolę. Na przykład można zaimportować ASP.NET aplikacji sieci web i wyznaczyć ją jako rolę sieci web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Dodawanie roli do usługi w chmurze platformy Azure
Poniższe kroki prowadzą użytkownika przez dodawanie roli sieci web lub procesu roboczego do projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**rozwiń węzeł projektu

1. Kliknij prawym przyciskiem myszy węzeł **Role,** aby wyświetlić menu kontekstowe. Z menu kontekstowego wybierz polecenie **Dodaj**, a następnie wybierz istniejącą rolę sieci Web lub rolę procesu roboczego z bieżącego rozwiązania lub utwórz projekt roli sieci Web lub procesu roboczego. Można również wybrać odpowiedni projekt, taki jak projekt aplikacji sieci web ASP.NET, i skojarzyć go z projektem roli.

   ![Opcje menu, aby dodać rolę do projektu usługi w chmurze platformy Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Usuwanie roli z usługi w chmurze platformy Azure
Poniższe kroki prowadzą użytkownika przez usunięcie roli sieci web lub procesu roboczego z projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**rozwiń węzeł projektu

1. Rozwiń węzeł **Role.**

1. Kliknij prawym przyciskiem myszy węzeł, który chcesz usunąć, a następnie z menu kontekstowego wybierz polecenie **Usuń**.

   ![Opcje menu, aby dodać rolę do usługi w chmurze platformy Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Odczytywanie roli w projekcie usługi w chmurze platformy Azure
Jeśli usuniesz rolę z projektu usługi w chmurze, ale później zdecydujesz się dodać rolę z powrotem do projektu, dodawane są tylko deklaracja roli i podstawowe atrybuty, takie jak punkty końcowe i informacje diagnostyczne. Żadne dodatkowe zasoby lub odwołania `ServiceDefinition.csdef` nie są `ServiceConfiguration.cscfg` dodawane do pliku lub do pliku. Jeśli chcesz dodać te informacje, musisz ręcznie dodać je z powrotem do tych plików.

Na przykład można usunąć rolę usługi sieci web, a później zdecydujesz się dodać tę rolę z powrotem do rozwiązania. Jeśli to zrobisz, wystąpi błąd. Aby zapobiec temu błędowi, `<LocalResources>` należy dodać element pokazany w `ServiceDefinition.csdef` następującym pliku XML z powrotem do pliku. Użyj nazwy roli usługi sieci web, która została dodana z powrotem do projektu jako część atrybutu nazwa dla ** \<LocalStorage>** element. W tym przykładzie nazwa roli usługi sieci web to **WCFServiceWebRole1**.

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
- [Konfigurowanie ról usługi w chmurze platformy Azure za pomocą programu Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
