This is based entirely on [cbold/dehyrated](https://hub.docker.com/r/cbolt/dehydrated/) with additional support for AWS Route53.

## Example Usage - dns

docker run -it --rm \
  --name dehydrated \
  -e 'STAGE=true' \
  -e 'CHALLENGE_TYPE=dns-01',
  -e 'PROVIDER=route53',
  -e 'LEXICON_ROUTE53_USERNAME=$AWS_ACCESS_KEY',
  -e 'LEXICON_ROUTE53_TOKEN=$AWS_SECRET_ACCESS_KEY',
  -v '</path/to/data>/certs:/data/certs' \
  -v '</path/to/data>/haproxy:/data/haproxy' \
  -v '</path/to/data>/accounts:/data/accounts' \
  -v '</path/to/data>/www:/var/www/dehydrated' \
  -v '</path/to/data>/domains.txt:/etc/dehydrated/domains.txt' \
  cbolt/dehydrated
