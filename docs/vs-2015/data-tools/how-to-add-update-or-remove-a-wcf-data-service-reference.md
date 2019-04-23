---
title: 'Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e7f70808ff91ec32ef52deedc05724f9bac3f7d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079147"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *sług* umożliwia dostęp do co najmniej jeden projekt [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Użyj **Dodaj odwołanie do usługi** okno dialogowe, aby wyszukać [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] w bieżącym rozwiązaniu lokalnie, w sieci lokalnej lub w Internecie.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>Dodawanie odwołania do usługi  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Aby dodać odwołanie do usługi zewnętrznej  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, który chcesz dodać usługę do, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.  
  
     **Dodaj odwołanie do usługi** pojawi się okno dialogowe.  
  
2. W **adres** , wprowadź adres URL dla usługi, a następnie kliknij **Przejdź** wyszukiwania dla usługi. Jeśli usługa implementuje zabezpieczenia nazwę i hasło użytkownika, może się monit o nazwę użytkownika i hasło.  
  
    > [!NOTE]
    >  Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.  
  
     Możesz również wybrać adres URL z **adres** listy, w którym przechowywane są poprzednie 15 adresów URL, pod którymi — znaleziono metadane prawidłową usługę.  
  
     Pasek postępu jest wyświetlana podczas wyszukiwania. Zatrzymać wyszukiwania w dowolnym momencie, klikając **zatrzymać**.  
  
3. W **usług** listy, rozwiń węzeł usługi, który chcesz użyć, a następnie wybierz zestaw jednostek.  
  
4. W **Namespace** wprowadź obszar nazw, który chcesz użyć dla odwołania.  
  
5. Kliknij przycisk **OK** można dodać odwołania do projektu.  
  
     Klient usługi (proxy) jest generowany, a metadane opisujące usługi są dodawane do pliku app.config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Aby dodać odwołanie do usługi w bieżącym rozwiązaniu  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, który chcesz dodać usługę do, a następnie kliknij przycisk **Dodaj odwołanie do usługi**.  
  
     **Dodaj odwołanie do usługi** pojawi się okno dialogowe.  
  
2. Kliknij przycisk **odnajdywanie**.  
  
     Wszystkie usługi (zarówno [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] i usługi WCF) w bieżącym rozwiązaniu są dodawane do **usług** listy.  
  
3. W **usług** listy, rozwiń węzeł usługi, który chcesz użyć, a następnie wybierz zestaw jednostek.  
  
4. W **Namespace** wprowadź obszar nazw, który chcesz użyć dla odwołania.  
  
5. Kliknij przycisk **OK** można dodać odwołania do projektu.  
  
     Klient usługi (proxy) jest generowany, a metadane opisujące usługi są dodawane do pliku app.config.  
  
## <a name="updating-a-service-reference"></a>Aktualizowanie odwołania do usługi  
 Modelu Entity Data Model, aby uzyskać [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] czasami ulegnie zmianie. W takim przypadku należy zaktualizować odwołania do usługi.  
  
#### <a name="to-update-a-service-reference"></a>Aby zaktualizować odwołania do usługi  
  
- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij przycisk **odwołanie do usługi aktualizacji**.  
  
     Okno dialogowe postępu jest wyświetlana, gdy odwołanie jest aktualizowany z oryginalnej lokalizacji, a klient usługi zostanie ponownie wygenerowany, aby odzwierciedlały zmiany w metadanych.  
  
## <a name="removing-a-service-reference"></a>Usuwanie odwołań usługi  
 Odwołanie do usługi jest już używany, możesz go usunąć z rozwiązania.  
  
#### <a name="to-remove-a-service-reference"></a>Aby usunąć odwołanie do usługi  
  
- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy odwołanie do usługi, a następnie kliknij przycisk **Usuń**.  
  
     Klient usługi zostanie usunięty z rozwiązania, a metadane opisujące usługi zostaną usunięte z pliku app.config.  
  
    > [!NOTE]
    >  Wszelki kod, który odwołuje się odwołanie do usługi, należy usunąć ręcznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
