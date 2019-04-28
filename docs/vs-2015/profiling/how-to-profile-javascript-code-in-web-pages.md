---
title: 'Instrukcje: Profiluj kod JavaScript na stronach sieci Web | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c3a6526732ffa398d25b0c3c5d73fed771f6958
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443467"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Instrukcje: Profiluj kod JavaScript na stronach sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania może zbierać dane wydajności dla kodu JavaScript, która jest wykonywana w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sieci Web aplikacji, dowolnej strony sieci Web lub aplikacji JavaScript przy użyciu Instrumentacji, metoda profilowania.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Internet Explorer 8 lub nowszy.  
  
> [!WARNING]
> Aby profilować kod JavaScript w aplikacjach Windows Store, zobacz jeden z następujących tematów:  
> 
> - [Synchronizacja funkcji JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [synchronizacja funkcji JavaScript na urządzeniu zdalnym](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   - [Analizowanie danych synchronizacja funkcji JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   - 
  
 Aby utworzyć sesję wydajności, można użyć Kreatora profilowania. Określ metody instrumentacji, a następnie określ JavaScript profilowania opcję na stronie Instrumentacji w oknie dialogowym właściwości sesji wydajności.  
  
 Po określeniu profilowanie plików JavaScript, kod JavaScript, który wykonuje w przeglądarce i [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod, który jest wykonywany na serwerze są profilowane.  
  
- Aby uzyskać [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, zarówno kod JavaScript, który jest wykonywany w przeglądarce i [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod, który jest wykonywany na serwerze są profilowane.  
  
- Dla dowolnej strony sieci Web kod JavaScript, który jest wykonywany w przeglądarce jest profilowana.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci Web platformy ASP.NET  
  
1. W [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], otwórz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projektu sieci Web.  
  
2. Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie kreatora wydajności, należy określić **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.  
  
4. Na drugiej stronie kreatora, upewnij się, że bieżący projekt jest zaznaczony na liście elementów docelowych, a następnie kliknij przycisk **dalej.**  
  
5. Na trzeciej stronie kreatora wybierz **Profiluj kod JavaScript** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
6. Na czwartej stronie kreatora kliknij **Zakończ** do uruchomienia aplikacji sieci Web w przeglądarce.  
  
7. Przetestuj funkcjonalność, która powinny być profilowane.  
  
8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilowanie kodu JavaScript w stronach sieci Web lub aplikacji JavaScript  
  
1. Otwórz [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2. Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie kreatora wydajności, należy określić **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.  
  
4. Na drugiej stronie kreatora kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **dalej.**  
  
5. Na trzeciej stronie kreatora:  
  
    1. Wpisz adres URL strony w **jakim adresem URL lub ścieżką będzie działała aplikacja sieci** pole.  
  
    2. Wybierz **Profiluj kod JavaScript** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
6. Na czwartej stronie kreatora kliknij **Zakończ** można uruchomić strony sieci Web w przeglądarce.  
  
7. Przetestuj funkcjonalność, która powinny być profilowane.  
  
8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.
