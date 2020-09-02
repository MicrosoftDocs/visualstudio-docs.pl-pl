---
title: Wskazówki dotyczące obsługi dla izolowanych aplikacji powłoki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159271"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Wytyczne dotyczące obsługi aplikacji w programie Shell (izolowanym)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas dystrybucji aplikacji powłoki izolowanej programu Visual Studio należy mieć możliwość udostępnienia aktualizacji oprogramowania dla aplikacji po jej zainstalowaniu. Aby to zrobić, należy zainstalować aplikację przy użyciu pliku Instalatora firmy Microsoft (MSI). Ten rodzaj instalacji umożliwia rozpowszechnianie aktualizacji oprogramowania przez firmę Microsoft przez pobranie sieci Web i używanie ich przez klientów bez konieczności interwencji niestandardowej.  
  
## <a name="servicing-requirements"></a>Wymagania dotyczące obsługi  
 Można upewnić się, że instalacja powłoki izolowanej może zezwalać na aktualizacje, upewniając się, że program instalacyjny spełnia następujące trzy kryteria.  
  
### <a name="redistribute-by-using-an-msi"></a>Ponowna dystrybucja przy użyciu pliku MSI  
 Aby przeprowadzić dystrybucję aplikacji, należy użyć pliku MSI, ponieważ plik MSI zachowuje tożsamość produktu i sprawdza, czy aplikacja ma fizyczną lokalizację na komputerze klienckim. Moduły scalania (pliki. msm) nie zapewniają takich gwarancji i nie powinny być używane.  
  
### <a name="accounting-for-custom-actions"></a>Ewidencjonowanie aktywności dla akcji niestandardowych  
 Niestandardowe akcje są dyrektywami instalacji niestandardowej w programie Instalatora. Akcje niestandardowe zmieniają parametry, takie jak lokalizacje plików, ustawienia rejestru, ustawienia użytkownika lub inne elementy instalacji. Akcje niestandardowe mogą manipulować danymi w czasie instalacji.  
  
 W przypadku używania akcji niestandardowych w programie instalacyjnym należy upewnić się, że każda akcja niestandardowa czasu instalacji musi mieć odpowiadającą jej akcję niestandardową, aby cofnąć akcję, gdy użytkownik odinstaluje aplikację. Jeśli program instalacyjny nie poda odpowiedniej akcji odinstalowania, usunięcie aplikacji pozostanie częściowo zainstalowane.  
  
- Akcja niestandardowa, która opiera się na określonej wersji pliku lub wartości skrótu, zakończy się niepowodzeniem, gdy aktualizacje oprogramowania zmienią te wersje lub wartości skrótu. W takim przypadku akcja niestandardowa musi ręcznie zaktualizować te wartości. Dodatkowy problem występuje, jeśli wersje pliku lub wartości skrótów są współużytkowane przez wersje produktu. Należy unikać tej zależności wszędzie tam, gdzie to możliwe.  
  
### <a name="accounting-for-shared-files"></a>Ewidencjonowanie aktywności dla udostępnionych plików  
 Pliki udostępnione mają takie same nazwy i są zainstalowane w tej samej lokalizacji przez wiele produktów. Te produkty mogą się różnić w zależności od wersji, jednostki składowania (SKU) lub obu, a produkty mogą współistnieć na danym komputerze. Jednak udostępnione pliki tworzą problemy z obsługą z kilku powodów:  
  
- Aktualizacja udostępnionych plików może powodować problemy ze zgodnością aplikacji, ponieważ aktualizacja jednej aplikacji może zmienić wersję pliku używanego przez drugą aplikację, która nie została zaktualizowana. Instalatory dla produktów, które współużytkują pliki, mają odwołania do udostępnionych plików. W związku z tym odinstalowanie produktu nie ma wpływu na pliki udostępnione poza zmniejszeniem liczby zainstalowanych wystąpień.  
  
- Instalator programu Quick Fix Engineering (QFE) przywraca wersje plików do wersji produktów obsługiwanych przez Instalatora QFE. Ten proces może spowodować przerwanie aplikacji, która dostarczyła zaktualizowany plik udostępniony.
