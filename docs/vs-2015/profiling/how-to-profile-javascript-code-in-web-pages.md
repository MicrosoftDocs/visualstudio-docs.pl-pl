---
title: 'Instrukcje: profilowanie kodu JavaScript na stronach sieci Web | Microsoft Docs'
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
ms.openlocfilehash: aa504e961ed8e592f5e3df84ff7a688fa2398200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688145"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Instrukcje: profilowanie kodu JavaScript na stronach internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania może zbierać dane dotyczące wydajności kodu JavaScript, który jest wykonywany w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, dowolnej stronie sieci Web lub aplikacji JavaScript przy użyciu metody profilowania Instrumentacji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Internet Explorer 8 lub nowszy.  
  
> [!WARNING]
> Aby profilować skrypty JavaScript w aplikacjach ze sklepu Windows, zobacz jeden z następujących tematów:  
> 
> - [Funkcja języka JavaScript](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) chronometraż [funkcji JavaScript na urządzeniu zdalnym](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   - [Analizuj dane chronometrażu funkcji JavaScript](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   - 
  
 Aby utworzyć sesję wydajności, można użyć Kreatora profilowania. Określ metodę instrumentacji, a następnie określ opcję profilowania JavaScript na stronie Instrumentacja okna dialogowego właściwości dla sesji wydajności.  
  
 Po określeniu profilowania JavaScript, zarówno kod JavaScript wykonywany w przeglądarce, jak i [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod wykonywany na serwerze są profilowane.  
  
- W przypadku [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web kod języka JavaScript wykonywany w przeglądarce i [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod wykonywany na serwerze są profilowane.  
  
- W przypadku dowolnej strony sieci Web kod JavaScript wykonywany w przeglądarce jest profilowany.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci Web ASP.NET  
  
1. W programie [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] Otwórz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Projekt sieci Web.  
  
2. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie Kreatora wydajności Określ metodę profilowania **Instrumentacji** , a następnie kliknij przycisk **dalej**.  
  
4. Na drugiej stronie kreatora upewnij się, że na liście elementów docelowych wybrano bieżący projekt, a następnie kliknij przycisk **Dalej.**  
  
5. Na trzeciej stronie kreatora zaznacz pole wyboru **profil JavaScript** , a następnie kliknij przycisk **dalej**.  
  
6. Na czwartej stronie kreatora kliknij przycisk **Zakończ** , aby uruchomić aplikację sieci Web w przeglądarce.  
  
7. Wykonuj funkcje, które chcesz profilować.  
  
8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Aby profilować kod JavaScript na poszczególnych stronach sieci Web lub w aplikacjach JavaScript  
  
1. Otwórz plik [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.  
  
3. Na pierwszej stronie Kreatora wydajności Określ metodę profilowania **Instrumentacji** , a następnie kliknij przycisk **dalej**.  
  
4. Na drugiej stronie kreatora kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **Dalej.**  
  
5. Na trzeciej stronie kreatora:  
  
    1. Wpisz adres URL strony w polu **adres URL lub ścieżka uruchomi aplikację** .  
  
    2. Zaznacz pole wyboru **profil JavaScript** , a następnie kliknij przycisk **dalej**.  
  
6. Na czwartej stronie kreatora kliknij przycisk **Zakończ** , aby uruchomić stronę sieci Web w przeglądarce.  
  
7. Wykonuj funkcje, które chcesz profilować.  
  
8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.
