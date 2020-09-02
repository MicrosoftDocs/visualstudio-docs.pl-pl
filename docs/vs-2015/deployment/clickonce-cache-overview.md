---
title: Omówienie pamięci podręcznej ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151665"
---
# <a name="clickonce-cache-overview"></a>Przegląd pamięci podręcznej w technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wszystkie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje, niezależnie od tego, czy są zainstalowane lokalnie czy hostowane online, są przechowywane na komputerze klienckim w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] *pamięci podręcznej*aplikacji. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Pamięć podręczna jest rodziną ukrytych katalogów w katalogu ustawień lokalnych folderu dokumenty i ustawienia bieżącego użytkownika. Ta pamięć podręczna zawiera wszystkie pliki aplikacji, w tym zestawy, pliki konfiguracji, ustawienia aplikacji i użytkownika oraz katalog danych. Pamięć podręczna jest również odpowiedzialna za Migrowanie katalogu danych aplikacji do najnowszej wersji. Aby uzyskać więcej informacji o migracji danych, zobacz [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Przez udostępnienie pojedynczej lokalizacji magazynu aplikacji program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przejmuje zadanie zarządzania fizyczną instalacją aplikacji od użytkownika. Pamięć podręczna ułatwia również izolowanie aplikacji przez utrzymywanie zestawów i plików danych dla wszystkich aplikacji i ich odrębnych wersji oddzielnie od siebie. Na przykład podczas uaktualniania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji ta wersja i jej zasoby danych są dostarczane z ich własnymi katalogami w pamięci podręcznej.  
  
## <a name="cache-storage-quota"></a>Przydział pamięci podręcznej  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje hostowane w trybie online są ograniczone ilością miejsca, w którym mogą one zajmować się limit przydziału, który ogranicza rozmiar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pamięci podręcznej. Rozmiar pamięci podręcznej dotyczy wszystkich aplikacji online użytkownika; jedna częściowo zaufana aplikacja online może zajmować połowę przestrzeni przydziału. Zainstalowane aplikacje nie są ograniczone przez rozmiar pamięci podręcznej i nie są wliczane do limitu pamięci podręcznej. W przypadku wszystkich [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji pamięć podręczna zachowuje tylko bieżącą wersję i wcześniej zainstalowaną wersję.  
  
 Domyślnie komputery klienckie mają 250 MB magazynu dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji online. Pliki danych nie są wliczane do tego limitu. Administrator systemu może zwiększyć lub zmniejszyć ten limit przydziału na określonym komputerze klienckim, zmieniając klucz rejestru HKEY_CURRENT_USER \Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, który jest wartością DWORD, która wyraża rozmiar pamięci podręcznej w kilobajtach. Na przykład, aby zmniejszyć rozmiar pamięci podręcznej do 50 MB, należy zmienić tę wartość na 51200.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
