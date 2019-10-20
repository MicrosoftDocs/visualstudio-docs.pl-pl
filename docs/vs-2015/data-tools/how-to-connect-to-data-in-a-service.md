---
title: 'Instrukcje: łączenie się z danymi w usłudze | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654689"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Porady: łączenie z danymi w usłudze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz połączyć aplikację z danymi zwróconymi z usługi, uruchamiając [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) i wybierając pozycję **Usługa** na stronie **Wybierz typ źródła danych** .

 Po zakończeniu działania kreatora do projektu zostanie dodane odwołanie do usługi i jest ono natychmiast dostępne w [oknie źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

> [!NOTE]
> Elementy wyświetlane w oknie **źródła danych** są zależne od informacji zwracanych przez usługę. Niektóre usługi mogą nie zapewniać wystarczającej ilości informacji dla **Kreatora konfiguracji źródła danych** , aby utworzyć obiekty możliwe do powiązania. Na przykład, jeśli usługa zwraca zestaw danych bez typu, nie są wyświetlane żadne elementy w **oknie źródła danych** po zakończeniu pracy kreatora. Wynika to z faktu, że niewpisane zestawy danych nie udostępniają schematu, więc Kreator nie ma wystarczających informacji do utworzenia źródła danych.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Aby połączyć aplikację z usługą

1. W menu **dane** kliknij polecenie **Dodaj nowe źródło danych**.

2. Wybierz pozycję **Usługa** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

3. Wprowadź adres usługi, której chcesz użyć, lub kliknij przycisk **odkryj** , aby zlokalizować usługi w bieżącym rozwiązaniu, a następnie kliknij przycisk **Przejdź**.

4. Opcjonalnie można wpisać nową **przestrzeń nazw** zamiast wartości domyślnej.

    > [!NOTE]
    > Kliknij przycisk **Zaawansowane** , aby otworzyć okno [dialogowe Konfigurowanie odwołania do usługi](../data-tools/configure-service-reference-dialog-box.md).

5. Kliknij przycisk **OK** , aby dodać odwołanie do usługi do projektu.

6. Kliknij przycisk **Zakończ**.

     Źródło danych zostanie dodane do okna **źródła danych** .

## <a name="next-steps"></a>Następne kroki

#### <a name="to-add-functionality-to-your-application"></a>Aby dodać funkcjonalność do aplikacji

- Wybierz element w oknie **źródła danych** i przeciągnij go na formularz, aby utworzyć powiązane kontrolki. Aby uzyskać więcej informacji, zobacz [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
 [Powiązywanie kontrolek WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Windows Communication Foundation usługami i usługi danych programu WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
