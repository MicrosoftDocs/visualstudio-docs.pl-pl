---
title: 'Obszar testowy 6: Usuwanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1498566e1afeaf1517b7ae3bd62297444c828888
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766307"
---
# <a name="test-area-6-delete"></a>Obszar testowy 6: usuwanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten obszar testowy wtyczki kontroli źródła obejmuje akcje usuwania.  
  
 Kontrola źródła reaguje na usuwanie akcji w **Eksploratora rozwiązań**.  
  
 Poniżej przedstawiono listę elementów, które można usunąć:  
  
- Pliki  
  
- Foldery  
  
- Projekt  
  
  W zależności od typu projektu może mieć możliwość **Usuń** projektu (pozostawia pliki na dysku) lub **Usuń** projektu (spowoduje to usunięcie plików na dysku). Każda z tych akcji spowoduje usunięcie projektu lub elementu z **Eksploratora rozwiązań**.  
  
## <a name="expected-behavior"></a>Oczekiwane zachowanie  
 To oczekiwane zachowanie dla przypadków testowych, w obszarze badania delete:  
  
-   Usunięty element nie jest już widoczna w ramach **Eksploratora rozwiązań**.  
  
-   Element nadrzędny usuniętego projektu lub element jest wyewidencjonowany, zgodnie z potrzebami (prawdopodobnie wraz z monitem o.)  
  
-   Po usunięciu zaznaczenia lub dodano element, nie ma w **oczekujące elementy do zaewidencjonowania** okna.  
  
-   Element nadal istnieje w magazynie kontroli źródła, nawet po usunięciu i musi ręcznie przeczyścić.  
  
|Akcja|Kroki testu|Oczekiwanych wyników, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Usuń projekt klienta|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Usuń cały projekt z rozwiązania|Typowe oczekiwane zachowanie.|  
|Usuń pusty plik|1.  Utwórz projekt klienta.<br />2.  Dodaj plik zero bajtów do projektu.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Wybierz plik, usuń go.|Typowe oczekiwane zachowanie.|  
|Usuń folder z plikami|1.  Utwórz rozwiązanie pojedynczego projektu.<br />2.  Dodaj folder.<br />3.  Dodaj jeden plik do folderu.<br />4.  Dodaj rozwiązanie do kontroli źródła.<br />5.  Zapoznaj się z projektu, aby uniknąć monity.<br />6.  Usuń folder.|Typowe oczekiwane zachowanie.|  
|Usuwanie projektu sieci Web systemu plików|1.  Utwórz projekt sieci Web systemu plików (Użyj przycisk Przeglądaj, aby określić ścieżkę UNC).<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Usuń cały projekt z rozwiązania.<br />4.  Powtórz kroki od 1 do 3 dla lokalnego projektu sieci Web (korzysta z różnych ścieżek za pośrednictwem kodu, ale ma ten sam interfejs zewnętrzny i zachowanie).|Typowe oczekiwane zachowanie.|  
|Usuwanie pliku z projektem sieci Web systemu plików|1.  Utwórz projekt sieci Web systemu plików.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Usuń plik z projektu.<br />4.  Powtórz kroki od 1 do 3 dla lokalnego projektu sieci Web (korzysta z różnych ścieżek za pośrednictwem kodu, ale ma ten sam interfejs zewnętrzny i zachowanie).|Typowe oczekiwane zachowanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

