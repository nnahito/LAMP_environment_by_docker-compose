# ========================================
# PHP-fpm用のCentOSイメージ
# ========================================
FROM centos:8

# CentOSを最新に
RUN yum clean all
RUN yum update -y
RUN yum upgrade -y

# タイムゾーンをJSTに
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# 言語を日本語に
RUN echo "LANG=ja_JP.UTF-8" | tee /etc/sysconfig/i18n

# php7.4のリポジトリが変わっているので利用できるようにする
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
RUN yum -y install https://rpms.remirepo.net/enterprise/remi-release-8.rpm

RUN dnf -y install dnf-utils

# php7.4のインストール
RUN dnf module reset php:remi-7.4
RUN dnf module install -y php:remi-7.4

# phpからMySQLを扱うプラグインのインストール
RUN yum install -y php-mysqlnd

# Socketファイルの置き場所フォルダがデフォルトでないので作成しておく
RUN mkdir -p /var/run/php-fpm/

CMD ["/usr/sbin/php-fpm", "-F"]