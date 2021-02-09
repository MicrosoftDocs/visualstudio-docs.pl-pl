---
title: 'Porady: łączenie z danymi w usłudze'
description: Połącz aplikację z danymi zwracanymi z usługi, uruchamiając Kreatora konfiguracji źródła danych i wybierając pozycję Usługa na stronie wybierz typ źródła danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: d8e3692f376a502a2cd924fa9604eddab445333f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858764"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Instrukcje: łączenie się z danymi w usłudze

Możesz połączyć aplikację z danymi zwróconymi z usługi, uruchamiając [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png) i wybierając pozycję **Usługa** na stronie **Wybierz typ źródła danych** .

Po zakończeniu działania kreatora do projektu zostanie dodane odwołanie do usługi i jest ono natychmiast dostępne w [oknie źródła danych](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Elementy wyświetlane w oknie **źródła danych** są zależne od informacji zwracanych przez usługę. Niektóre usługi mogą nie zapewniać wystarczającej ilości informacji dla **Kreatora konfiguracji źródła danych** , aby utworzyć obiekty możliwe do powiązania. Na przykład, jeśli usługa zwraca zestaw danych bez typu, nie są wyświetlane żadne elementy w oknie **źródła danych** po zakończeniu pracy kreatora. Wynika to z faktu, że niewpisane zestawy danych nie udostępniają schematu, więc Kreator nie ma wystarczających informacji do utworzenia źródła danych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Aby połączyć aplikację z usługą

1. W menu **dane** kliknij polecenie **Dodaj nowe źródło danych**.

2. Wybierz pozycję **Usługa** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

3. Wprowadź adres usługi, której chcesz użyć, lub kliknij przycisk **odkryj** , aby zlokalizować usługi w bieżącym rozwiązaniu, a następnie kliknij przycisk **Przejdź**.

4. Opcjonalnie można wpisać nową **przestrzeń nazw** zamiast wartości domyślnej.

    > [!NOTE]
    > Kliknij przycisk **Zaawansowane** , aby otworzyć okno [dialogowe Konfigurowanie odwołania do usługi](../data-tools/configure-service-reference-dialog-box.md).

5. Kliknij przycisk **OK** , aby dodać odwołanie do usługi do projektu.

6. Kliknij przycisk **Finish** (Zakończ).

     Źródło danych zostanie dodane do okna **źródła danych** .

## <a name="next-steps"></a>Następne kroki

Aby dodać funkcjonalność do aplikacji, wybierz element w oknie **źródła danych** i przeciągnij go na formularz, aby utworzyć powiązane kontrolki. Aby uzyskać więcej informacji, zobacz [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Powiązywanie kontrolek WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Usługi Windows Communication Foundation i usługi danych programu WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
