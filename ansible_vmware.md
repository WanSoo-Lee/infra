https://autoattack.tistory.com/20?category=890242

pypi.org
pyvmomi-7.0.1.tar.gz

# gzip -d /tmp/pyvmomi-7.0.1.tar.gz
# tar -xvf /tmp/pyvmomi-7.0.1.tar
# cd /tmp/pyvmomi-7.0.1
# python setup.py install


# vi /tmp/Making_VMware.yml

- name: Create VMware
  vmware_guest:
    hostname: 10.10.10.10                        // vCenter IP
    username: administrator@vsphere.local        // vCenter 로그인ID
    password: Vmware1!                           // vCenter 로그인PW
    folder: /vm                                  // VMware 생성 폴더
    name: Ansible_VM                             // VMware 이름
    state: poweredon                             // VMware 생성 후, 전원ON (반대는 powerdoff)
    guest_id: centos64Guest                      // GuestOS 호환성 종류 (다르면 부팅 불가함)
    esxi_hostname: 10.10.10.20                   // Vmware가 위치할 ESXi IP
    disk:                                        // 연결 Disk 정보
    - size_gb: 10
      type: thin
      datastore: datastore1
    hardware:                                     // 연결 CPU/MEM 정보
      memory_mb: 512
      num_cpus: 4

    cdrom:                                               // 연결 CPU/MEM 정보
      - controller_type: ide                             // cdrom 장치 Type
        controller_number: 0                             // 컨트롤러 번호 (특별한 이유가 없다면 0부터 시작)
        unit_number: 0                                   // cdrom 장치 번호 (컨트롤러 번호 사유와 동일)
        state: present                                   // cdrom 상태
        type: iso                                        // cdrom 연결 미디어 종류
        iso_path: "[Datastore1]/CentOS_V7_X86.iso"       // ISO 경로

# ansible-playbook Making_VMware.yml -vvv


# vi /tmp/Making_VMware.sh

#!/bin/bash
  echo -n "vCenter_IP : "; read vCenter_IP
  echo -n "vCenter_ID : "; read vCenter_ID
  echo -n "vCenter_PW : "; read vCenter_PW
  echo -n "Guest_Hostname : "; read Guest_Hostname
  echo -n "Guest_IP : "; read Guest_IP
  echo -n "Guest_SM : "; read Guest_SM
  echo -n "Guest_GW : "; read Guest_GW

# ansible-playbook /tmp/MakeVM_VMware.yml -vvv -e "vCenter_IP=$vCenter_IP vCenter_ID=$vCenter_ID vCenter_PW=$vCenter_PW Guest_Hostname=$Guest_Hostname Guest_IP=$Guest_IP Guest_SM=$Guest_SM Guest_GW=$Guest_GW"

echo 명령어를 사용하여 각각의 필요한 변수를 사용자 입력을 통해 할당받고, Playbook 실행 시에 이 변수들을 자동으로 입력되도록 하는 내용이다. 중요한 것은 #ansible-playbook과 -e 옵션을 함께 사용해야 하는 것이다.
