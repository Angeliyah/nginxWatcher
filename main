#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <unistd.h>
#include <iostream>
#include <netdb.h>
#include <net/if.h>
#include <arpa/inet.h>
#include <sys/ioctl.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <cstdlib>
#define IP_SIZE		16
bool charComp(char a[],char b[])
{
    int n = 0;
    if(strlen(a) != strlen(b)) //判断两数组/字符串的长度是否相等，不相等就肯定不会有数组/字符串相等了
        return 0;
    else
    {
        while(a[n]!='\0' && b[n]!='\0')
        {
          if(a[n] == b[n])
                n++;
            else
                return 0;  
        }
    }
    return 1;
}




// 根据域名获取ip
int get_ip_by_domain(const char *domain, char *ip)
{
	char **pptr;
	struct hostent *hptr;
 
	hptr = gethostbyname(domain);
	if(NULL == hptr)
	{
		printf("gethostbyname error for host:%s/n", domain);
		return -1;
	}
 
	for(pptr = hptr->h_addr_list ; *pptr != NULL; pptr++)
	{
		if (NULL != inet_ntop(hptr->h_addrtype, *pptr, ip, IP_SIZE) )
		{
			return 0; // 只获取第一个 ip
		}
	}
 
	return -1;
}
 


int main(void)
{
	using namespace std;
	char ip[IP_SIZE];
        char curIp[IP_SIZE];
	const char *test_domain = "cloudy.gnu.hk";
	get_ip_by_domain(test_domain, ip);
	while (1==1)
	       {
		system("/bin/sleep 5");
		get_ip_by_domain(test_domain, curIp);
		if(charComp(ip, curIp)==0)
			{
			system("/bin/systemctl restart nginx");
	
			}
	
	       }
	return 0;
}

