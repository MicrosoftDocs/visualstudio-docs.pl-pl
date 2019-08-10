---
title: 'Instrukcje: Tworzenie skojarzeń plików dla aplikacji ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0526351d2b3e2c223aacbe0e58d9ee39bd1b19c4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924556"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Instrukcje: Tworzenie skojarzeń plików dla aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikacje mogą być skojarzone z jednym lub więcej rozszerzeniami nazw plików, dzięki czemu aplikacja zostanie uruchomiona automatycznie, gdy użytkownik otworzy plik tych typów. Dodawanie obsługi rozszerzenia nazwy pliku do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji jest proste.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Aby utworzyć skojarzenia plików dla aplikacji ClickOnce

1. Utwórz aplikację normalnie lub Użyj istniejącej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]

2. Otwórz manifest aplikacji za pomocą edytora tekstu lub XML, takiego jak Notatnik.

3. `assembly` Znajdź element. Aby uzyskać więcej informacji, zobacz [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

4. Jako element podrzędny `assembly` elementu `fileAssociation` Dodaj element. `fileAssociation` Element ma cztery atrybuty:

   - `extension`: Rozszerzenie nazwy pliku, które ma zostać skojarzone z aplikacją.

   - `description`: Opis typu pliku, który będzie wyświetlany w powłoce systemu Windows.

   - `progid`: Ciąg unikatowo identyfikujący typ pliku, aby oznaczyć go w rejestrze.

   - `defaultIcon`: Ikona, która ma być używana dla tego typu pliku. Ikona musi być dodana jako zasób pliku w manifeście aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Dołącz plik danych do aplikacji](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)ClickOnce.

     Aby zapoznać się z `file` przykładem `fileAssociation` elementów i, zobacz [ \<fileAssociation > element](../deployment/fileassociation-element-clickonce-application.md).

5. Jeśli chcesz skojarzyć więcej niż jeden typ pliku z aplikacją, Dodaj dodatkowe `fileAssociation` elementy. Należy zauważyć, `progid` że atrybut powinien być różny dla każdego.

6. Po zakończeniu pracy z manifestem aplikacji ponownie podpisz manifest. Można to zrobić z wiersza polecenia, używając programu *Mage. exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Aby uzyskać więcej informacji, zobacz [plik Mage. exe (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Zobacz także
- [\<fileAssociation, element >](../deployment/fileassociation-element-clickonce-application.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)