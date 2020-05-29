---
title: Omówienie pamięci podręcznej ClickOnce | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7abeeec4a640119e3089c795ac529a10f8dc09
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182628"
---
# <a name="clickonce-cache-overview"></a>Omówienie pamięci podręcznej w technologii ClickOnce
Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje, niezależnie od tego, czy są zainstalowane lokalnie czy hostowane online, są przechowywane na komputerze klienckim w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *pamięci podręcznej*aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Pamięć podręczna jest rodziną ukrytych katalogów w katalogu ustawień lokalnych folderu dokumenty i ustawienia bieżącego użytkownika. Ta pamięć podręczna zawiera wszystkie pliki aplikacji, w tym zestawy, pliki konfiguracji, ustawienia aplikacji i użytkownika oraz katalog danych. Pamięć podręczna jest również odpowiedzialna za Migrowanie katalogu danych aplikacji do najnowszej wersji. Aby uzyskać więcej informacji o migracji danych, zobacz [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Przez udostępnienie pojedynczej lokalizacji magazynu aplikacji program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przejmuje zadanie zarządzania fizyczną instalacją aplikacji od użytkownika. Pamięć podręczna ułatwia również izolowanie aplikacji przez utrzymywanie zestawów i plików danych dla wszystkich aplikacji i ich odrębnych wersji oddzielnie od siebie. Na przykład podczas uaktualniania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji ta wersja i jej zasoby danych są dostarczane z ich własnymi katalogami w pamięci podręcznej.

## <a name="cache-storage-quota"></a>Przydział pamięci podręcznej
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikacje hostowane w trybie online są ograniczone ilością miejsca, w którym mogą one zajmować się limit przydziału, który ogranicza rozmiar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pamięci podręcznej. Rozmiar pamięci podręcznej dotyczy wszystkich aplikacji online użytkownika; jedna częściowo zaufana aplikacja online może zajmować połowę przestrzeni przydziału. Zainstalowane aplikacje nie są ograniczone przez rozmiar pamięci podręcznej i nie są wliczane do limitu pamięci podręcznej. W przypadku wszystkich [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji pamięć podręczna zachowuje tylko bieżącą wersję i wcześniej zainstalowaną wersję.

 Domyślnie komputery klienckie mają 250 MB magazynu dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji online. Pliki danych nie są wliczane do tego limitu. Administrator systemu może zwiększyć lub zmniejszyć ten limit przydziału na określonym komputerze klienckim, zmieniając klucz rejestru **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment\onlineappquotainkb**, który jest wartością DWORD, która wyraża rozmiar pamięci podręcznej w kilobajtach. Na przykład, aby zmniejszyć rozmiar pamięci podręcznej do 50 MB, należy zmienić tę wartość na 51200.

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)