---
title: 'Instrukcje: Uwzględnianie pliku danych w aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 470ee530a61ecba5c1acd40be88c469fee6d4f5e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596272"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Instrukcje: Uwzględnianie pliku danych w aplikacji ClickOnce
Każdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalowania aplikacji jest przypisany do katalogu danych na dysku lokalnym komputera docelowego, gdzie aplikacja można zarządzać swoimi danymi. Pliki danych może zawierać pliki dowolnego typu: pliki tekstowe, pliki XML lub nawet bazy danych Microsoft Access (*.mdb*) plików. Poniższe procedury pokazują, jak dodać plik danych dowolnego typu do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Aby dołączyć plik danych przy użyciu Mage.exe

1. Dodaj plik danych do katalogu aplikacji z użyciem usług rest plików aplikacji.

    Zazwyczaj będzie katalog etykietą bieżąca wersja wdrożenia katalogu aplikacji — na przykład v1.0.0.0.

2. Zaktualizuj manifest aplikacji do listy plików danych.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Wykonanie tego zadania ponownie utworzy listę plików w manifeście aplikacji, a także automatycznie wygeneruje sygnatury skrótu.

3. Otwórz manifest aplikacji w preferowanym tekstu lub edytora XML i Znajdź `file` element ostatnio dodane pliku.

    Jeśli został dodany plik XML o nazwie `Data.xml`, plik będzie wyglądać podobnie jak w poniższym przykładzie kodu.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Dodaj atrybut `type` do tego elementu i dostarczyć wartość `data`.

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Ponownie podpisać manifest aplikacji przy użyciu certyfikatu lub parę kluczy, a następnie ponownie podpisać manifest wdrożenia.

    Należy ponownie podpisać manifest wdrożenia, ponieważ jego skrót manifest aplikacji została zmieniona.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Aby dołączyć plik danych przy użyciu MageUI.exe

1.  Dodaj plik danych do katalogu aplikacji z użyciem usług rest plików aplikacji.

2.  Zazwyczaj będzie katalog etykietą bieżąca wersja wdrożenia katalogu aplikacji — na przykład v1.0.0.0.

3.  Na **pliku** menu, kliknij przycisk **Otwórz** otworzyć manifest aplikacji.

4.  Wybierz **pliki** kartę.

5.  W polu tekstowym w górnej części karty wprowadź katalog, który zawiera pliki aplikacji, a następnie kliknij przycisk **wypełniania**.

     Plik danych zostaną wyświetlone w siatce.

6.  Ustaw **typ pliku** wartość plik danych do **danych**.

7.  Zapisz manifest aplikacji, a następnie ponowne podpisywanie pliku.

     *MageUI.exe* wyświetli monit o ponowne podpisywanie pliku.

8.  Ponownie podpisać manifest wdrożenia

     Należy ponownie podpisać manifest wdrożenia, ponieważ jego skrót manifest aplikacji została zmieniona.

## <a name="see-also"></a>Zobacz także
- [Dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)