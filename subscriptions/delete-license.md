---
title: Usuwanie przypisań w portalu administracyjnym subskrypcji | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: Dowiedz się, jak Administratorzy mogą usuwać przypisania subskrypcji w portalu administratora subskrypcji programu Visual Studio
ms.openlocfilehash: c4e55a18bb172588bf1daf777aeee8fee1dca02b
ms.sourcegitcommit: f8d14fab194fcb30658f23f700da07d35ffc9d4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89561354"
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


