---
title: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF
description: Zapoznaj się z tematem Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych Windows Communication Foundation (WCF).
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6e6c289038c3f8cb9d1586ae4a1f7a84b563239f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436436"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF

::: moniker range="vs-2017"
*Odwołanie do usługi* umożliwia projektowi dostęp do co najmniej jednego elementu [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Użyj okna dialogowego **Dodaj odwołanie do usługi** , aby wyszukać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w bieżącym rozwiązaniu, lokalnie, w sieci lokalnej lub w Internecie.
::: moniker-end
::: moniker range=">=vs-2019"
Można użyć węzła **usługi połączone** w **Eksplorator rozwiązań** , aby uzyskać dostęp do **Microsoft WCF Web Service Reference Provider** , co umożliwia zarządzanie odwołaniami do usługi danych Windows Communication Foundation (WCF).
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Dodawanie odwołania do usługi WCF

### <a name="to-add-a-reference-to-an-external-service"></a>Aby dodać odwołanie do usługi zewnętrznej

::: moniker range="vs-2017"

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

   Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

1. W polu **adres** wprowadź adres URL usługi, a następnie kliknij przycisk **Przejdź** , aby wyszukać usługę. Jeśli usługa implementuje zabezpieczenia nazwy użytkownika i hasła, może zostać wyświetlony monit o podanie nazwy użytkownika i hasła.

    > [!NOTE]
    > Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

     Możesz również wybrać adres URL z listy **adres** , który przechowuje poprzednie 15 adresów URL, na których znaleziono prawidłowe metadane usługi.

     Podczas wykonywania wyszukiwania zostanie wyświetlony pasek postępu. Wyszukiwanie można zatrzymać w dowolnym momencie, klikając przycisk **Zatrzymaj**.

1. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

1. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

1. Kliknij przycisk **OK** , aby dodać odwołanie do projektu.

     Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. W **Eksplorator rozwiązań** kliknij dwukrotnie lub naciśnij węzeł **usługi połączone** .

   Zostanie otwarta karta **Konfigurowanie usług** .

1. Wybierz **Microsoft WCF Web Service Reference Provider**.

   Zostanie wyświetlone okno dialogowe **Konfigurowanie odwołania do usługi sieci Web WCF** .

   ![Zrzut ekranu przedstawiający okno dialogowe Dostawca usługi sieci Web WCF](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. W polu **Identyfikator URI** wprowadź adres URL usługi, a następnie kliknij przycisk **Przejdź** , aby wyszukać usługę. Jeśli usługa implementuje zabezpieczenia nazwy użytkownika i hasła, może zostać wyświetlony monit o podanie nazwy użytkownika i hasła.

    > [!NOTE]
    > Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

     Możesz również wybrać adres URL z listy **identyfikatorów URI** , który przechowuje poprzednie 15 adresów URL, na których znaleziono prawidłowe metadane usługi.

     Podczas wykonywania wyszukiwania zostanie wyświetlony pasek postępu. Wyszukiwanie można zatrzymać w dowolnym momencie, klikając przycisk **Zatrzymaj**.

1. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

1. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

1. Kliknij przycisk **Zakończ** , aby dodać odwołanie do projektu.

     Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku *app.config* .

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Aby dodać odwołanie do usługi w bieżącym rozwiązaniu

::: moniker range="vs-2017"

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

    Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

1. Kliknij pozycję **Odnajdź**.

    Wszystkie usługi ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do listy **usług** .

1. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

1. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

1. Kliknij przycisk **OK** , aby dodać odwołanie do projektu.

    Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. W **Eksplorator rozwiązań** kliknij dwukrotnie lub naciśnij węzeł **usługi połączone** . 

   Zostanie otwarta karta **Konfigurowanie usług** .

1. Wybierz **Microsoft WCF Web Service Reference Provider**.

   Zostanie wyświetlone okno dialogowe **Konfigurowanie odwołania do usługi sieci Web WCF** .

1. Kliknij pozycję **Odnajdź**.

    Wszystkie usługi ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do listy **usług** .

1. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

1. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

1. Kliknij przycisk **Zakończ** , aby dodać odwołanie do projektu.

    Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku *app.config* .

::: moniker-end

## <a name="update-a-service-reference"></a>Aktualizowanie odwołania do usługi

Entity Data Model [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] czasami zmienia się. W takim przypadku należy zaktualizować odwołanie do usługi.

### <a name="to-update-a-service-reference"></a>Aby zaktualizować odwołanie do usługi

- W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij pozycję **Aktualizuj odwołanie do usługi**.

     Zostanie wyświetlone okno dialogowe postęp, gdy odwołanie zostanie zaktualizowane z oryginalnej lokalizacji, a klient usługi zostanie wygenerowany ponownie w celu odzwierciedlenia wszelkich zmian w metadanych.

## <a name="remove-a-service-reference"></a>Usuń odwołanie do usługi

Jeśli odwołanie do usługi nie jest już używane, można je usunąć z rozwiązania.

### <a name="to-remove-a-service-reference"></a>Aby usunąć odwołanie do usługi

- W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij pozycję **Usuń**.

     Klient usługi zostanie usunięty z rozwiązania, a metadane opisujące usługę zostaną usunięte z pliku *app.config* .

    > [!NOTE]
    > Każdy kod, który odwołuje się do odwołania do usługi, musi zostać usunięty ręcznie.

## <a name="see-also"></a>Zobacz też

- [Usługi Windows Communication Foundation i usługi danych programu WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
