---
title: 'Instrukcje: wyświetlanie dokumentów skryptów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f923ab0447f1ac7d57e84d94f0ab442d912d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189599"
---
# <a name="how-to-view-script-documents"></a>Porady: wyświetlanie dokumentów skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

We wcześniejszych wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] skrypty po stronie klienta generowane przez skrypt po stronie serwera pojawiły się w oknie Eksplorator skryptów. Okno Eksplorator skryptów jest często ukryte, dzięki czemu dostępność skryptu po stronie klienta nie zawsze jest oczywista.  
  
 W programie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] pliki skryptów po stronie klienta generowane przez skrypt po stronie serwera pojawiają się w Eksplorator rozwiązań, który jest domyślnie widoczny. Okno Eksploratora skryptów zostało usunięte.  
  
 Pliki skryptów po stronie klienta są widoczne tylko wtedy, gdy jesteś w trybie debugowania lub w trybie przerwania. Są one wyświetlane w węźle **dokumenty skryptu** .  
  
 Pliki skryptów po stronie serwera są zawsze widoczne. Są one wyświetlane w **\<Website Pathname>** węźle. Nazwa węzła jest podobna do poniższego przykładu: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie serwera  
  
1. W **Eksplorator rozwiązań**Otwórz **\<Website Pathname>** węzeł.  
  
2. Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.  
  
     Plik skryptu po stronie serwera zostanie otwarty w oknie źródła.  
  
### <a name="to-view-a-client-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie klienta  
  
1. W **Eksplorator rozwiązań**Otwórz węzeł **dokumenty skryptu** .  
  
2. Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.  
  
     Plik skryptu po stronie klienta zostanie otwarty w oknie źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
