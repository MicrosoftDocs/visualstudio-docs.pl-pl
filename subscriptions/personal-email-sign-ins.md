---
title: Osobiste wiadomości e-mail wyświetlane w VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Subskrypcje programu Visual Studio — Dlaczego widzę adresy Hotmail i Gmail dla subskrybentów?
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605755"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Subskrypcje programu Visual Studio — Dlaczego widzę adresy Hotmail i Gmail dla subskrybentów?
Po przeprowadzeniu migracji z witryny Volume Licensing Service Center (VLSC) do nowego [portalu administratora subskrypcji](https://manage.visualstudio.com)programu Visual Studio Administratorzy mogli stwierdzić, że adres e-mail logowania dla niektórych subskrybentów pokazuje adres e-mail innej firmy adres, taki jak Hotmail, Gmail lub Yahoo.  Aby uzyskać więcej informacji, zapoznaj się z [tym wideo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Przyczyna
Ten scenariusz występuje ze względu na procesy logowania skojarzone ze starszym doświadczeniem subskrybenta MSDN. Użytkownicy zostali zmigrowani z witryny Volume License Service Center (VLSC) do portalu administracyjnego subskrypcji programu Visual Studio bez żadnych modyfikacji. Administratorzy mogą nie wiedzieć, że użytkownicy korzystali z kont osobistych w celu uzyskania dostępu do korzyści z subskrypcji. Przed migracją subskrybentów programu Visual Studio, które zostały wykonane w 2016, były dwie akcje wymagane do pomyślnego użycia Visual Studio Subscription:
1. Administrator "przypisał" subskrypcję do indywidualnego subskrybenta przy użyciu służbowego adresu e-mail.
2. Subskrybent "aktywowany" w ramach subskrypcji.

Podczas procesu aktywacji subskrybenta: Konto Microsoft (MSA) było wymagane do zalogowania się. Jeśli subskrybent nie podjął próby przeprowadzenia konta służbowego (np. tasha@contoso.com) jako elementu MSA, może utworzyć nowy element MSA lub wykorzystać istniejący. W związku z tym "adres E-mail logowania" jest inny niż przypisany do adresu E-mail.

> [!NOTE]
> Nowe środowisko subskrybenta w [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) systemie obsługuje typy tożsamości: służbowe i konto Microsoft (MAA).

Na koniec ponieważ migracja przez administratora dotyczyła danych z usługi VLSC w odniesieniu do adresu E-mail subskrybenta, aby wypełnić nowe środowisko zarządzania subskrybentami, niedawno zmigrowani Administratorzy mogli zobaczyć te wcześniej niezauważalne konta osobiste ze względu na zmiany w interfejsie użytkownika, które te informacje były widoczne.

## <a name="solution"></a>Rozwiązanie
Aby rozwiązać ten problem, należy edytować informacje o subskrybencie w celu zaktualizowania ich adresów e-mail logowania.  Zmiany mogą być wprowadzane dla indywidualnych subskrybentów lub zbiorczo. Aby uzyskać pełne informacje, zobacz [Edytowanie subskrypcji](edit-license.md).

##  <a name="next-steps"></a>Następne kroki
- Jeśli Zaktualizowano adresy e-mail subskrybentów, można powiadomić ich, że informacje logowania zostały zmienione.  Otrzymają także wiadomość e-mail z zaktualizowanymi informacjami.
- Przydatne może być odfiltrowanie [listy subskrybentów](search-license.md) w organizacji, aby wyszukać wszelkie adresy e-mail logowania, które mogą wymagać zmiany.  

