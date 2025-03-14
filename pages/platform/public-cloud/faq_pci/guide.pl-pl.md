---
title: FAQ
excerpt: 'FAQ dla instancji Public Cloud'
slug: public-cloud-faq
section: 'Pierwsze kroki'
order: 3
---

> [!primary]
> Tłumaczenie zostało wygenerowane automatycznie przez system naszego partnera SYSTRAN. W niektórych przypadkach mogą wystąpić nieprecyzyjne sformułowania, na przykład w tłumaczeniu nazw przycisków lub szczegółów technicznych. W przypadku jakichkolwiek wątpliwości zalecamy zapoznanie się z angielską/francuską wersją przewodnika. Jeśli chcesz przyczynić się do ulepszenia tłumaczenia, kliknij przycisk „Zaproponuj zmianę” na tej stronie.
>

**Ostatnia aktualizacja z dnia 06/09/2021**

## FAQ Public Cloud

### Jak połączyć się z instancją Public Cloud?

Połączenie realizowane jest za pomocą kilku kluczy SSH, które chcesz skonfigurować podczas tworzenia instancji Public Cloud.

Zapraszamy do zapoznania się z przewodnikiem [Tworzenie pierwszej instancji Public Cloud i łączenie się z nią](../public-cloud-pierwsze-kroki/).

### Zgubiłem lub chcę zmienić klucz SSH, jak to zrobić?

Jeśli nie możesz się zalogować po utracie klucza prywatnego, zmień klucz publiczny Twojej instancji zmieniając go w tryb "Rescue".

Zapoznaj się z przewodnikiem [Zmiana klucza SSH w przypadku utraty](../zmiana_klucza_ssh_w_przypadku_utraty/).

### Jakie są możliwości kopii zapasowej mojej instancji?

W każdej chwili możesz utworzyć kopię zapasową instancji w Panelu klienta OVHcloud. Dzięki kopii zapasowej możesz przywrócić instancję z pierwotną konfiguracją lub ją odtworzyć.

Zapoznaj się z przewodnikiem dotyczącym [Tworzenia kopii zapasowej instancji](../kopia_zapasowa_instancji/).

### Jak tworzyć użytkowników OpenStack i zarządzać nimi?  

Aby móc korzystać z interfejsów API Horizon lub OpenStack, należy utworzyć użytkownika OpenStack. Możesz utworzyć nieograniczoną liczbę.

Zapoznaj się z przewodnikiem [Tworzenie i usuwanie użytkownika OpenStack](../tworzenie-i-usuwanie-uzytkownika-openstack/).

### Jakie są metody fakturowania za usługę Public Cloud?

Opłata za wykorzystane zasoby jest pobierana między pierwszym a piątym dniem każdego miesiąca i dotyczy zasobów wykorzystanych w poprzednim miesiącu. Jeśli wybrałeś opłatę miesięczną, abonament za przyszły miesiąc jest fakturowany w tym samym czasie co zużycie zasobów godzinowych za poprzedni miesiąc (instancje, Object Storage). W przypadku przejścia na abonament miesięczny, naliczana jest natychmiast proporcjonalna opłata za korzystanie z danego zasobu przez dni pozostałe do końca bieżącego miesiąca.
Każda instancja jest płatna, jeśli nie została usunięta z Panelu klienta OVHcloud.
Możesz monitorować zużycie zasobów dzięki prognozom uzyskiwanym na podstawie historii wcześniejszego zużycia. Możesz również wybrać opcję fakturowania każdego projektu Public Cloud oddzielnie, co pozwoli na ewentualne refakturowanie usługi w ramach Twojej firmy.

Aby zmienić model rozliczenia na inny, zapoznaj się z naszym przewodnikiem [Zmiana typu rozliczenia z godzinowego na miesięczne dla instancji Public Cloud](../zmiana-typu-rozliczenia/).

### Jak zmieniać parametry instancji w sytuacji, gdy potrzebuję więcej lub mniej zasobów?

Każda instancja może zostać zmieniona na wyższy model z tej samej gamy w Panelu klienta, klikając `edytuj`{.action} na stronie instancji. Możesz również zmienić jej rozmiar na niższy model, jeśli została ona uruchomiona z opcją "flex". Opcja ta wymaga rozmiaru dysku 50 GB w przypadku wszystkich modeli i umożliwia zmianę rozmiaru dysku na obie strony.
W każdym przypadku zmiana rozmiaru instancji wiąże się z jej ponownym uruchomieniem.

### Czy instancje Public Cloud są kompatybilne z cloud-init?

Tak, obrazy cloud dostarczane przez OVHcloud zawierają skrypty cloud-init, które umożliwiają personalizację instancji w momencie ich uruchomienia. Infrastruktura dostarcza informacje o personalizacji instancji za pośrednictwem serwera metadanych, z którym bezpośrednio komunikuje się cloud-init.

### Czy można wykonać kopię zapasową serwerów Public Cloud?

Tak, możesz w dowolnym momencie i bez ograniczeń tworzyć kopie zapasowe instancji.  Kopie zapasowe są przechowywane i fakturowane podobnie jak obrazy w "Private Image". Dzięki API OpenStack będziesz mógł je pobrać z infrastruktury OVHcloud lub z innych projektów.

Zapoznaj się z przewodnikiem dotyczącym [Tworzenia kopii zapasowej instancji](../kopia_zapasowa_instancji/).

### Czy można dynamicznie zwiększać rozmiar wolumenu jednocześnie zapisując dane na dysku?

Nie, przed zwiększeniem rozmiaru wolumenu, należy odłączyć dysk.

### Ile dodatkowych wolumenów mogę przypisać do każdej instancji?

Możesz przypisać do 26 dodatkowych wolumenów do każdej instancji.

### W jaki sposób moje serwery są zabezpieczone?

OVHcloud chroni całą swoją infrastrukturę dzięki swojemu unikalnemu rozwiązaniu anty-DDoS. Ponadto możesz stworzyć grupy bezpieczeństwa OpenStack. Jest to odpowiednik zapory zarządzany bezpośrednio na poziomie infrastruktury OpenStack, przed Twoimi instancjami.

Zapraszamy do zapoznania się z przewodnikiem [Konfiguracja grupy zabezpieczeń](../konfiguracja_grupy_zabezpieczen/).

Zabezpieczenia te, w połączeniu z zabezpieczeniami, które możesz zainstalować na Twoich serwerach, zwiększą niezawodność wdrożenia.

### Jak mogę utworzyć prywatną sieć łączącą moje serwery?

Public Cloud jest zintegrowany z rozwiązaniem SDN (software-defined network). Umożliwia ona dynamiczne tworzenie prywatnych sieci, a następnie podłączenie ich do instancji za pośrednictwem Panelu klienta lub API.
Prywatne sieci opierają się na technologii vRack używanej również przez inne usługi firmy, takie jak Private Cloud lub serwery dedykowane. Dzięki temu możesz w sposób odizolowany i bezpieczny połączyć wszystkie elementy infrastruktury z OVHcloud.

Zapraszamy do zapoznania się z przewodnikiem [Konfiguracja usługi vRack Public Cloud](https://docs.ovh.com/gb/en/public-cloud/public-cloud-vrack/) (EN).

### Czy mogę zmienić publiczny adres IP mojej instancji?

Publiczne adresy IP są automatycznie przypisane do instancji i dlatego nie można ich zmienić. Zalecamy użycie adresu IP Failover, aby zarządzać publicznym adresem IP instancji. W ten sposób, bez względu na publiczny adres przypisany automatycznie do instancji, możesz dodać jeden lub kilka adresów IP failover do Twojej instancji.

Zapraszamy do zapoznania się z przewodnikiem [Wykupienie adresu IP Failover](../wykupienie_adresu_ip_failover/).

## Sprawdź również

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
