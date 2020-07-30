---
title: Usuwanie przypisań subskrypcji w portalu administracyjnym subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: Dowiedz się, jak Administratorzy mogą usuwać przypisania subskrypcji
ms.openlocfilehash: 4f952f574132afbd405c82c75fcddfc952bffb48
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2020
ms.locfileid: "87434273"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Usuwanie przypisań w subskrypcjach programu Visual Studio
Gdy Subskrybenci nie wymagają już subskrypcji programu Visual Studio, na przykład gdy opuszczają firmę, ukończą projekt lub przełączają się do nowej roli zadania, można usunąć swoją subskrypcję i przypisać ją do innej osoby. Należy pamiętać, że po ponownym przypisaniu subskrypcji nie wszystkie korzyści dla subskrybenta zostaną zresetowane.  Nowy użytkownik będzie mógł przejąć wszystkie nieprzejęte klucze i wyświetlić poprzednio zażądane klucze, ale limity **nie** są resetowane.  W przypadku organizacji z umowami Enterprise Agreement (EA) wszystkie korzyści, które były używane przez oryginalnego użytkownika, takie jak szkolenia Pluralsight, zostaną zresetowane. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Usuwanie przypisania subskrypcji
1. Kliknij nazwę abonenta, który chcesz usunąć. Aby wybrać wielu subskrybentów do usunięcia, możesz kliknąć okrąg z lewej strony nazwy subskrybenta, aby wybrać każdy z nich.  Alternatywnie można przytrzymać wciśnięty klawisz **Ctrl** i kliknąć każdego abonenta, który chcesz usunąć. Aby usunąć wielu subskrybentów, kliknij pierwszy, a następnie naciśnij klawisz **SHIFT** i kliknij ostatni.  Naciśnij **kombinację klawiszy Ctrl + A** , aby wybrać i usunąć wszystkich subskrybentów. 
2. Aby usunąć wybranych abonentów, kliknij przycisk **Usuń**.
3. Gdy zostanie wyświetlony komunikat z prośbą o potwierdzenie usunięcia, kliknij przycisk **OK**.
   > [!div class="mx-imgBorder"]
   > ![Usuwanie subskrybentów](_img/delete-license/delete-subscribers.png "Wybierz użytkowników, które chcesz usunąć, a następnie kliknij pozycję Usuń. Możesz użyć klawiszy CTRL i Shift, aby wybrać wielu subskrybentów.")

   > [!NOTE]
   > Usuwanie zbiorcze przy użyciu szablonu jest niedostępne. W przypadku organizacji, które zarządzają przypisaniami subskrypcji za poorednictwem grup zabezpieczeń Azure Active Directory, zobacz [nasz artykuł](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) , aby uzyskać więcej informacji na temat sposobu usuwania.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Chcesz zmienić subskrypcję bez jej usuwania?  Dowiedz się, jak [edytować subskrypcje](edit-license.md)
- Aby uzyskać pomoc dotyczącą znajdowania określonej subskrypcji, zapoznaj się z tematem [Wyszukiwanie w ramach subskrypcji](search-license.md).
- Chcesz utworzyć listę wszystkich Twoich subskrypcji?  Zapoznaj się z tematem [Eksportowanie subskrypcji](exporting-subscriptions.md).


