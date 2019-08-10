---
title: 'Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych w technologii WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da8555d4246d2177b3d97eeef8d24c7b4a22b31d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925636"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF
*Odwołanie do usługi* umożliwia projektowi dostęp do co najmniej jednego [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]elementu. Użyj okna dialogowego **Dodaj odwołanie do usługi** , aby wyszukać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] w bieżącym rozwiązaniu, lokalnie, w sieci lokalnej lub w Internecie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Dodawanie odwołania do usługi

### <a name="to-add-a-reference-to-an-external-service"></a>Aby dodać odwołanie do usługi zewnętrznej

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

     Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

2. W polu **adres** wprowadź adres URL usługi, a następnie kliknij przycisk **Przejdź** , aby wyszukać usługę. Jeśli usługa implementuje zabezpieczenia nazwy użytkownika i hasła, może zostać wyświetlony monit o podanie nazwy użytkownika i hasła.

    > [!NOTE]
    > Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

     Możesz również wybrać adres URL z listy **adres** , który przechowuje poprzednie 15 adresów URL, na których znaleziono prawidłowe metadane usługi.

     Podczas wykonywania wyszukiwania zostanie wyświetlony pasek postępu. Wyszukiwanie można zatrzymać w dowolnym momencie, klikając przycisk **Zatrzymaj**.

3. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

4. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

5. Kliknij przycisk **OK** , aby dodać odwołanie do projektu.

     Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku *App. config* .

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Aby dodać odwołanie do usługi w bieżącym rozwiązaniu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać usługę, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

    Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

2. Kliknij przycisk **odkryj**.

    Wszystkie usługi ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do listy **usług** .

3. Na liście **usługi** rozwiń węzeł usługi, która ma zostać użyta, a następnie wybierz zestaw jednostek.

4. W polu **przestrzeń nazw** wprowadź przestrzeń nazw, która ma być używana dla odwołania.

5. Kliknij przycisk **OK** , aby dodać odwołanie do projektu.

    Zostanie wygenerowany klient usługi (proxy), a metadane opisujące usługę zostaną dodane do pliku *App. config* .

## <a name="update-a-service-reference"></a>Aktualizowanie odwołania do usługi
Entity Data Model [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] czasami zmienia się. W takim przypadku należy zaktualizować odwołanie do usługi.

### <a name="to-update-a-service-reference"></a>Aby zaktualizować odwołanie do usługi

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij pozycję **Aktualizuj odwołanie do usługi**.

     Zostanie wyświetlone okno dialogowe postęp, gdy odwołanie zostanie zaktualizowane z oryginalnej lokalizacji, a klient usługi zostanie wygenerowany ponownie w celu odzwierciedlenia wszelkich zmian w metadanych.

## <a name="remove-a-service-reference"></a>Usuń odwołanie do usługi
Jeśli odwołanie do usługi nie jest już używane, można je usunąć z rozwiązania.

### <a name="to-remove-a-service-reference"></a>Aby usunąć odwołanie do usługi

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij pozycję **Usuń**.

     Klient usługi zostanie usunięty z rozwiązania, a metadane opisujące usługę zostaną usunięte z pliku *App. config* .

    > [!NOTE]
    > Każdy kod, który odwołuje się do odwołania do usługi, musi zostać usunięty ręcznie.

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych programu WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)