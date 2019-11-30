# ========================================
# Apache用のCentOSイメージ
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

RUN export DOCKER_HOST=tcp://localhost:2375

# Apacheを入れる
RUN yum install -y httpd
RUN apachectl -v
RUN systemctl enable httpd.service
# RUN apachectl start

EXPOSE 80

CMD ["/usr/sbin/httpd", "-DFOREGROUND"]