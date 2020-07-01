---
title: 'Instrukcje: podpisywanie aplikacji i manifestów wdrożenia'
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e04827dd8d8d393af8bc3448df75a7503c8eec3
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769785"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Instrukcje: podpisywanie aplikacji i manifestów wdrożenia

Jeśli chcesz opublikować aplikację przy użyciu wdrożenia ClickOnce, manifesty aplikacji i wdrożenia muszą być podpisane za pomocą pary kluczy publiczny/prywatny i podpisane przy użyciu technologii Authenticode. Można podpisać manifesty przy użyciu certyfikatu z magazynu certyfikatów systemu Windows lub pliku klucza.

Aby uzyskać więcej informacji na temat wdrażania ClickOnce, zobacz [zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md).

Podpisywanie manifestów ClickOnce jest opcjonalne dla aplikacji opartych na programie *. exe*. Aby uzyskać więcej informacji, zobacz sekcję "Generowanie nieoznaczonych manifestów" w tym dokumencie.

Aby uzyskać informacje na temat tworzenia plików kluczy, zobacz [How to: Create a Public-Private Key pair](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> Program Visual Studio obsługuje tylko pliki kluczy wymiany informacji osobistych (PFX), które mają rozszerzenie *PFX* . Można jednak wybrać inne typy certyfikatów z magazynu certyfikatów systemu Windows bieżącego użytkownika, klikając **pozycję Wybierz ze sklepu** na stronie **podpisywanie** właściwości projektu.

## <a name="sign-using-a-certificate"></a>Logowanie przy użyciu certyfikatu

1. Przejdź do okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**). Na karcie **podpisywanie** wybierz pole wyboru **Podpisz manifesty ClickOnce** .

2. Kliknij przycisk **Wybierz ze sklepu** .

     Zostanie wyświetlone okno dialogowe **Wybierz certyfikat** i zostanie wyświetlona zawartość magazynu certyfikatów systemu Windows.

    > [!TIP]
    > Jeśli klikniesz **pozycję kliknij tutaj, aby wyświetlić właściwości certyfikatu**, zostanie wyświetlone okno dialogowe **Szczegóły certyfikatu** . To okno dialogowe zawiera szczegółowe informacje o certyfikacie i opcjach dodatkowych. Kliknij pozycję **Certyfikaty** , aby wyświetlić dodatkowe informacje pomocy.

3. Wybierz certyfikat, którego chcesz użyć do podpisania manifestów.

4. Dodatkowo można określić adres serwera znacznika czasowego w polu tekstowym **adres URL serwera znaczników czasu** . Jest to serwer, który zawiera sygnaturę czasową określającą, kiedy manifest został podpisany.

## <a name="sign-using-an-existing-key-file"></a>Podpisz przy użyciu istniejącego pliku klucza

1. Na stronie **podpisywanie** wybierz pole wyboru **Podpisz manifesty ClickOnce** .

2. Kliknij przycisk **Wybierz z pliku** .

     Zostanie wyświetlone okno dialogowe **Wybierz plik** .

3. W oknie dialogowym **Wybierz plik** przejdź do lokalizacji pliku klucza (*PFX*), którego chcesz użyć, a następnie kliknij przycisk **Otwórz**.

    > [!NOTE]
    > Ta opcja obsługuje tylko pliki z rozszerzeniem *PFX* . Jeśli masz plik klucza lub certyfikat w innym formacie, Zapisz go w magazynie certyfikatów systemu Windows i wybierz certyfikat opisany w poprzedniej procedurze. Wybrany cel certyfikatu powinien obejmować podpisywanie kodu.

     Pojawi się okno dialogowe **Wprowadź hasło, aby otworzyć plik** . (Jeśli plik *PFX* jest już przechowywany w magazynie certyfikatów systemu Windows lub nie jest chroniony hasłem, nie zostanie wyświetlony monit o wprowadzenie hasła).

4. Wprowadź hasło, aby uzyskać dostęp do pliku klucza, a następnie wybierz klawisz **Enter**.

> [!NOTE]
> Plik *PFX* nie może zawierać informacji o łańcuchu certyfikatów. Jeśli tak się dzieje, wystąpi następujący błąd importowania: **nie można odnaleźć certyfikatu i klucza prywatnego do odszyfrowania**. Aby usunąć informacje o łańcuchu certyfikatów, można użyć *certmgr. msc* i [wyłączyć opcję](/previous-versions/aa730868(v=vs.80)) **uwzględniania wszystkich certyfikatów** podczas eksportowania pliku *. pfx.

## <a name="sign-using-a-test-certificate"></a>Podpisywanie przy użyciu certyfikatu testowego

1. Na stronie **podpisywanie** wybierz pole wyboru **Podpisz manifesty ClickOnce** .

2. Aby utworzyć nowy certyfikat do testowania, kliknij przycisk **Utwórz certyfikat testowy** .

3. W oknie dialogowym **Tworzenie certyfikatu testowego** wprowadź hasło, aby pomóc w zabezpieczeniu certyfikatu testowego.

## <a name="generate-unsigned-manifests"></a>Generuj niepodpisane manifesty

Podpisywanie manifestów ClickOnce jest opcjonalne dla aplikacji opartych na programie *. exe*. W poniższych procedurach pokazano, jak generować niepodpisane manifesty ClickOnce.

> [!IMPORTANT]
> Niepodpisane manifesty mogą uprościć programowanie i testowanie aplikacji. Jednak niepodpisane manifesty wprowadzają znaczne zagrożenia bezpieczeństwa w środowisku produkcyjnym. Rozważ użycie niepodpisanych manifestów, jeśli aplikacja ClickOnce jest uruchamiana na komputerach w intranecie, które są całkowicie odizolowane od Internetu lub innych źródeł złośliwego kodu.

Domyślnie ClickOnce automatycznie generuje podpisane manifesty, chyba że co najmniej jeden plik jest wyraźnie wykluczony z wygenerowanego skrótu. Innymi słowy, opublikowanie aplikacji powoduje podpisywanie manifestów, jeśli wszystkie pliki są zawarte w skrócie, nawet jeśli pole wyboru **Podpisz manifesty ClickOnce** jest wyczyszczone.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Aby wygenerować niepodpisane manifesty i uwzględnić wszystkie pliki w wygenerowanym skrócie

1. Aby wygenerować niepodpisane manifesty zawierające wszystkie pliki w skrócie, należy najpierw opublikować aplikację ze podpisanymi manifestami. W związku z tym najpierw Podpisz manifesty ClickOnce, wykonując jedną z poprzednich procedur, a następnie Opublikuj aplikację.

2. Na stronie **podpisywanie** wyczyść pole wyboru **Podpisz manifesty ClickOnce** .

3. Zresetuj wersję publikacji tak, aby była dostępna tylko jedna wersja aplikacji. Domyślnie program Visual Studio automatycznie zwiększa numer wersji publikacji przy każdym publikowaniu aplikacji. Aby uzyskać więcej informacji, zobacz [How to: Set The ClickOnce Publish Version](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Opublikuj aplikację.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Aby wygenerować niepodpisane manifesty i wykluczyć jeden lub więcej plików z wygenerowanego skrótu

1. Na stronie **podpisywanie** wyczyść pole wyboru **Podpisz manifesty ClickOnce** .

2. Otwórz okno dialogowe **pliki aplikacji** i ustaw **skrót** do **wykluczenia** dla plików, które mają zostać wykluczone z wygenerowanego skrótu.

    > [!NOTE]
    > Wykluczenie pliku ze skrótu powoduje skonfigurowanie technologii ClickOnce do wyłączania automatycznego podpisywania manifestów, dlatego nie trzeba najpierw publikować ze podpisanymi manifestami, jak pokazano w poprzedniej procedurze.

3. Opublikuj aplikację.

## <a name="see-also"></a>Zobacz także

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Instrukcje: Tworzenie pary kluczy publiczny-prywatny](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md)
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
