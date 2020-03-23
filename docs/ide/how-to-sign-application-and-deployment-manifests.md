---
title: 'Jak: Podpisywanie manifestów aplikacji i wdrażania'
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf25301095ac5ff438514c37f61337e46342860
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596167"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Jak: Podpisywanie manifestów aplikacji i wdrażania

Jeśli chcesz opublikować aplikację przy użyciu clickonce wdrożenia, manifesty aplikacji i wdrażania muszą być podpisane za pomocą pary kluczy publicznych/prywatnych i podpisane przy użyciu technologii Authenticode. Manifesty można podpisać przy użyciu certyfikatu z magazynu certyfikatów systemu Windows lub pliku klucza.

Aby uzyskać więcej informacji na temat wdrażania ClickOnce, zobacz [ClickOnce zabezpieczeń i wdrażania](../deployment/clickonce-security-and-deployment.md).

Podpisywanie manifestów ClickOnce jest opcjonalne dla aplikacji opartych na *exe.* Aby uzyskać więcej informacji, zobacz sekcję "Generowanie niepodpisanych manifestów" tego dokumentu.

Aby uzyskać informacje dotyczące tworzenia plików kluczy, zobacz [Jak: Tworzenie pary kluczy publiczno-prywatnych](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> Program Visual Studio obsługuje tylko pliki kluczy programu Exchange (PFX) z rozszerzeniem *.pfx.* Można jednak wybrać inne typy certyfikatów z magazynu certyfikatów systemu Windows bieżącego użytkownika, klikając pozycję **Wybierz ze Sklepu** na stronie **Podpisywanie** właściwości projektu.

## <a name="sign-using-a-certificate"></a>Podpisywanie przy użyciu certyfikatu

1. Przejdź do okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości).** Na karcie **Podpisywanie** zaznacz pole wyboru **Podpisz manifesty clickonce.**

2. Kliknij przycisk **Wybierz ze sklepu.**

     Zostanie wyświetlone okno dialogowe **Wybieranie certyfikatu** i zostanie wyświetlona zawartość magazynu certyfikatów systemu Windows.

    > [!TIP]
    > Po kliknięciu **przycisku Kliknij tutaj, aby wyświetlić właściwości certyfikatu,** zostanie wyświetlone okno dialogowe **Szczegóły certyfikatu.** To okno dialogowe zawiera szczegółowe informacje o certyfikacie i dodatkowych opcjach. Kliknij **pozycję Certyfikaty,** aby wyświetlić dodatkowe informacje o pomocy.

3. Wybierz certyfikat, którego chcesz użyć do podpisania manifestów.

4. Ponadto można określić adres serwera sygnatury czasowej w polu tekstowym **URL serwera sygnatury czasowej.** Jest to serwer, który udostępnia sygnaturę czasową określającą, kiedy manifest został podpisany.

## <a name="sign-using-an-existing-key-file"></a>Podpisywanie przy użyciu istniejącego pliku klucza

1. Na stronie **Podpisywanie** zaznacz pole wyboru Podpisz pole wyboru **Podpisz manifesty ClickOnce.**

2. Kliknij przycisk **Wybierz z pliku.**

     Zostanie wyświetlone okno dialogowe **Wybieranie pliku.**

3. W oknie dialogowym **Wybieranie pliku** przejdź do lokalizacji pliku klucza (*.pfx*), którego chcesz użyć, a następnie kliknij przycisk **Otwórz**.

    > [!NOTE]
    > Ta opcja obsługuje tylko pliki, które mają rozszerzenie *.pfx.* Jeśli masz plik klucza lub certyfikat w innym formacie, przechowuj go w magazynie certyfikatów systemu Windows i wybierz certyfikat jest opisany w poprzedniej procedurze. Celem wybranego certyfikatu powinno być podpisywanie kodu.

     Zostanie wyświetlone okno dialogowe **Wprowadzanie hasła do otwierania pliku.** (Jeśli plik *.pfx* jest już przechowywany w magazynie certyfikatów systemu Windows lub nie jest chroniony hasłem, nie jest wyświetlany monit o wprowadzenie hasła).

4. Wprowadź hasło, aby uzyskać dostęp do pliku klucza, a następnie wybierz pozycję **Enter**.

> [!NOTE]
> Plik *.pfx* nie może zawierać informacji o łańcuchowaniu certyfikatów. Jeśli tak się stanie, wystąpi następujący błąd importu: **Nie można odnaleźć certyfikatu i klucza prywatnego do odszyfrowania**. Aby usunąć informacje o łańcuchach certyfikatów, można użyć *pliku Certmgr.msc* i [wyłączyć opcję](/previous-versions/aa730868(v=vs.80)) **Dołączanie wszystkich certyfikatów** podczas eksportowania pliku *.pfx.

## <a name="sign-using-a-test-certificate"></a>Podpisywanie przy użyciu certyfikatu testowego

1. Na stronie **Podpisywanie** zaznacz pole wyboru Podpisz pole wyboru **Podpisz manifesty ClickOnce.**

2. Aby utworzyć nowy certyfikat do testowania, kliknij przycisk **Utwórz certyfikat testu.**

3. W oknie dialogowym **Tworzenie certyfikatu testowego** wprowadź hasło, aby zabezpieczyć certyfikat testu.

## <a name="generate-unsigned-manifests"></a>Generowanie niepodpisanych manifestów

Podpisywanie manifestów ClickOnce jest opcjonalne dla aplikacji opartych na *exe.* Poniższe procedury pokazują, jak wygenerować niepodpisane manifesty ClickOnce.

> [!IMPORTANT]
> Niepodpisane manifesty mogą uprościć tworzenie i testowanie aplikacji. Jednak niepodpisane manifesty wprowadzają znaczne zagrożenia bezpieczeństwa w środowisku produkcyjnym. Należy rozważyć użycie niepodpisanych manifestów, jeśli aplikacja ClickOnce działa na komputerach w intranecie, który jest całkowicie odizolowany od Internetu lub innych źródeł złośliwego kodu.

Domyślnie ClickOnce automatycznie generuje podpisane manifesty, chyba że jeden lub więcej plików są wyraźnie wykluczone z wygenerowanego skrótu. Innymi słowy, publikowanie aplikacji powoduje podpisane manifesty, jeśli wszystkie pliki są zawarte w mieszaniu, nawet wtedy, gdy pole wyboru **Podpisz manifesty ClickOnce** jest wyczyszczone.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Aby wygenerować niepodpisane manifesty i uwzględnić wszystkie pliki w wygenerowanym mieszaniu

1. Aby wygenerować niepodpisane manifesty, które zawierają wszystkie pliki w mieszaniu, należy najpierw opublikować aplikację wraz z podpisanymi manifestami. W związku z tym najpierw podpisać ClickOnce manifestuje, wykonując jedną z poprzednich procedur, a następnie opublikować aplikację.

2. Na stronie **Podpisywanie** wyczyść pole wyboru Podpisz pole wyboru **Podpisuj manifesty ClickOnce.**

3. Zresetuj wersję publikowania, aby była dostępna tylko jedna wersja aplikacji. Domyślnie program Visual Studio automatycznie zwiększa numer poprawki wersji publikowania za każdym razem, gdy publikujesz aplikację. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie wersji publikowania ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Opublikuj aplikację.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Aby wygenerować niepodpisane manifesty i wykluczyć jeden lub więcej plików z wygenerowanego skrótu

1. Na stronie **Podpisywanie** wyczyść pole wyboru Podpisz pole wyboru **Podpisuj manifesty ClickOnce.**

2. Otwórz okno dialogowe **Pliki aplikacji** i ustaw skrót **do wykluczenia** dla plików, które chcesz wykluczyć z wygenerowanego skrótu. **Hash**

    > [!NOTE]
    > Wykluczając plik z skrótu konfiguruje ClickOnce, aby wyłączyć automatyczne podpisywanie manifestów, więc nie trzeba najpierw publikować z podpisanymi manifestami, jak pokazano w poprzedniej procedurze.

3. Opublikuj aplikację.

## <a name="see-also"></a>Zobacz też

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Jak: Tworzenie pary kluczy publiczno-prywatnych](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md)
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
