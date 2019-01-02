---
title: 'Instrukcje: Łączenie z danymi w usłudze'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 66a13ac6f23caa3e6ccf28d5d68c03b3fe7fdb4f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923877"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Instrukcje: Łączenie z danymi w usłudze

Łączenie aplikacji z danymi zwróconymi z usługi, uruchamiając [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png) i wybierając polecenie **usługi** na **wybierz typ źródła danych**strony.

Po zakończeniu działania kreatora, jest dodawany do projektu odwołanie do usługi i jest natychmiast dostępna w [okna źródeł danych](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Elementy, które pojawiają się w **źródeł danych** okna są zależne od informacji, zwracanemu przez usługę. Niektóre usługi mogą nie dostarczać wystarczających informacji dla **Kreatora konfiguracji źródła danych** do tworzenia obiektów, które można powiązać. Na przykład, jeśli usługa zwraca zestaw danych bez typu, żadne elementy nie są wyświetlane w **źródeł danych** okna po ukończeniu kreatora. Jest to spowodowane nietypizowanych zbiorów danych nie zapewniają schematu, dlatego Kreator nie ma wystarczających informacji, aby utworzyć źródło danych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Aby połączyć aplikację z usługą

1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.

2.  Wybierz **usługi** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

3.  Wprowadź adres usługi, o których chcesz używać, lub kliknij przycisk **odnajdź** lokalizowania usług w bieżącym rozwiązaniu, a następnie kliknij przycisk **Przejdź**.

4.  Opcjonalnie możesz wpisać nową **Namespace** zamiast wartości domyślne.

    > [!NOTE]
    > Kliknij przycisk **zaawansowane** otworzyć [okno dialogowe Konfigurowanie odwołania do usługi](../data-tools/configure-service-reference-dialog-box.md).

5.  Kliknij przycisk **OK** można dodać odwołanie do usługi do projektu.

6.  Kliknij przycisk **Zakończ**.

     Źródło danych jest dodawane do **źródeł danych** okna.

## <a name="next-steps"></a>Następne kroki

Aby dodać funkcje do aplikacji, wybierz element w **źródeł danych** okna i przeciągnij je na formularz, aby utworzyć formanty powiązane. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Powiązywanie kontrolek WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Communication Foundation i usługi WCF usług danych w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)