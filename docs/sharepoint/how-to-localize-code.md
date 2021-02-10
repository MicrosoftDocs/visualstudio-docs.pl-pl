---
title: 'Instrukcje: lokalizowanie kodu | Microsoft Docs'
description: Dowiedz się, jak zlokalizować kod w programie SharePoint, zamieniając zakodowane ciągi na wywołania GetGlobalResourceObject, metodę odwołującą się do zlokalizowanych zasobów.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e76b8cfb2e9fcb513905918bd4ae87524078f6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931646"
---
# <a name="how-to-localize-code"></a>Instrukcje: lokalizowanie kodu
  Kod nielokalny używa zakodowanych wartości ciągu. Aby zlokalizować ciągi kodu, zastąp je wywołaniami <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> , które jest metodą, która odwołuje się do zlokalizowanych zasobów.

## <a name="localize-code"></a>Lokalizowanie kodu

#### <a name="to-localize-code"></a>Aby zlokalizować kod

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla elementu projektu, a następnie wybierz polecenie **Dodaj**  >  **Moduł**.

     Wybierz szablon **plik zasobów** .

    > [!NOTE]
    > Pamiętaj, aby dodać plik zasobów do elementu projektu programu SharePoint, tak aby właściwość typ wdrożenia była dostępna. Ta właściwość jest wymagana w dalszej części tej procedury.

2. Nadaj plikowi zasobu języka domyślnego wybraną nazwę, która jest dołączana do rozszerzenia *resx* , np. *MyAppResources. resx*.

3. Powtórz kroki 1 i 2, aby dodać oddzielne pliki zasobów do elementu projektu programu SharePoint: jeden dla każdego zlokalizowanego języka.

     Użyj tej samej nazwy bazowej dla każdego zlokalizowanego pliku zasobów, ale Dodaj identyfikator kultury. Na przykład Nazwij plik niemiecki zlokalizowany zasób *MyAppResources.de-de. resx*.

4. Otwórz każdy plik zasobów i Dodaj zlokalizowane ciągi. Użyj tych samych identyfikatorów ciągów w każdym pliku.

5. Zmień wartość właściwości **typ wdrożenia** każdego pliku zasobu na **AppGlobalResource** , aby spowodować, że każdy plik zostanie wdrożony w folderze App_GlobalResources serwera.

6. Pozostaw wartość właściwości **Akcja kompilacji** każdego pliku jako **zasób osadzony**.

     Zasoby osadzone są kompilowane do biblioteki DLL projektu.

7. Skompiluj projekt, aby utworzyć satelitarne biblioteki DLL zasobów.

8. W **projektancie pakietów** wybierz kartę **Zaawansowane** , a następnie Dodaj zestaw satelicki.

9. W polu **Lokalizacja** Dołącz folder z identyfikatorem kultury do ścieżki lokalizacji, na przykład *de-de \\ \<Project Item Name>.resources.dll*.

10. Jeśli rozwiązanie nie odwołuje się już do zestawu System. Web, Dodaj odwołanie do niego i Dodaj dyrektywę w kodzie do <xref:System.Web> .

11. Znajdź wszystkie zakodowane ciągi w kodzie, które są widoczne dla użytkowników, takie jak tekst interfejsu użytkownika, błędy i tekst komunikatu. Zastąp je wywołaniem <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metody przy użyciu następującej składni:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Wybierz klawisz **F5** , aby skompilować i uruchomić aplikację.

13. W programie SharePoint Zmień język wyświetlania z domyślnego.

     Zlokalizowane ciągi pojawiają się w aplikacji. Aby wyświetlić zlokalizowane zasoby, na serwerze programu SharePoint musi być zainstalowany pakiet językowy zgodny z kulturą pliku zasobów.

## <a name="see-also"></a>Zobacz też
- [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)
- [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Instrukcje: Dodawanie pliku zasobów](../sharepoint/how-to-add-a-resource-file.md)
